---
layout: page
title: Adaptive Finite Element for Network Architecture Design
permalink: /nsfOAC/ANDeS/
---
### Introduction
A major overhead in the training process for deep neural networks is the architecture and hyperparameter search. Many architectures 
may be well-suited to any particular problem, and over-parameterized networks may provide little gains in accuracy for the increases 
in memory and compute costs. There is thus a desire for an adaptive algorithm which can efficiently find the minimal parameterization
(minimum network depth and width) for a desired accuracy (e.g., a mean-squared error loss $\mathcal{L}_\textrm{MSE}<\varepsilon_
\textrm{threshold}$ for a regression problem).

Our approach to an efficient algorithm for adaptive network design (ANDes) begins with the parallels between the Residual Network 
(ResNet) \cite{he2015deep} and forward Euler numerical integration. ResNets add skip connections, creating a layer evaluation defined 
by

$$ x_l = x_{l-1} + F_l(\theta_l,x_{l-1}) $$

where the state $x$ after the $l$-th layer is the sum of the previous state and the $l$-th layer output. This matches the forward 
Euler scheme
$$ x(t_n) = x(t_{n-1}) + \Delta t_n f\Bigl(x(t_{n-1})\Bigr) $$

This gives rise to the [Neural ODE](https://arxiv.org/abs/1512.03385), which instead treats the network as describing the first time derivative of a 
continuous ODE. Well-known ODE solvers (e.g., adaptive Runge-Kutta methods) can be used in 
the evaluation to adaptively trade off accuracy and computational speed. This greatly reduces the memory cost, as the parameters are 
used to describe the ODE, rather than each integration in the pseudo-time variable. Further, by describing Lipschitz-continuous ODEs 
through the use of Lipschitz nonlinearities (e.g., ReLU and tanh), the initial-value problem (i.e, evaluating the neural network) has 
unique solutions.

Unfortunately, the Neural ODE tends to learn more and more complicated ODEs as training progresses, leading the ODE solvers to choose 
very small timesteps and increasing the computational cost to evaluate. While there have been some [recent works](https://arxiv.org/abs/2002.02798) in regularizing the 
learned ODEs to require fewer solver evaluations, we turn our attention back towards neural 
networks as discretizations of the ODE.

By viewing ResNets instead as finite element methods (FEM) in time, we can generalize the forward Euler as a continuous FEM solution 
(e.g., continuous Galerkin methods) with interpolating polynomial degree 1. This allows us to leverage the body of work in a 
posteriori error analysis and adaptive FEM (e.g., for [mesh refinement](https://www.cambridge.org/core/journals/acta-numerica/article/an-optimal-control-approach-to-a-posteriori-error-estimation-in-finite-element-methods/5C67A03F528C6FA69F37A97DF5C3BE19)
and [optimal control](https://link.springer.com/article/10.1007/s10543-010-0270-8))to adapt the network architecture during training to guarantee improvement in performance. Further, we will be able 
to definitively find a point at which further training and refinement provides improvement below some threshold, and stop training.


### Width-based Method
It is well-known that using the ReLU activation function can result in a
piecewise-linear map across a layer. In short, a neuron receiving from a layer of ReLU-activated 
neurons has a value equal to the sum of several piecewise-linear functions which have slopes defined by the layer weights and kinks at 
the locations defined by the quotient of the biases and weights. Thus, the contribution of one neuron to the value of a neuron two 
layers down is a piecewise-linear function, and the total value of that neuron is a multivariate piecewise-linear function with each 
neuron two layers prior as its inputs.

With this relationship, we again generalize the piecewise-linear map to a FEM solution with linear polynomials. Instead of ReLU, we 
leverage the compact support of the typical FEM basis function, Lagrange polynomials. As in FEM, the output neuron's value is the sum 
of all basis functions. In this case, each basis function is defined as having a representative domain $[-1,1]$, which is then 
transformed through the affine transformations defined by the weights and biases. For the linear case, (i.e., the hat function)
The hat function locations and widths are explicitly controlled by the biases, with the endpoints of each hat aligning with
the peaks of its neighbors, as it does in FEM. The weight matrix now holds the interpolant node values for each piecewise linear map.

This formulation has two added upsides: (1) This allows us to perform a posteriori error analysis and add neurons with weights and 
biases designed to add basis functions where contributions to the error estimate are high. (2) The compact support allows us to 
easily identify out-of-distribution (OOD) inputs, as OOD inputs will result in an output of entirely zeros (or completely unchanged, 
for ResNets).


For ease of implementation (and avoiding the use of looped $\texttt{argwhere}$ calls), this can be implemented as a $\texttt{ReLU}$
composed with a $\texttt{min}$ of two linear functions:

$$
    y_{i,j}(x) = 
        W_{i,j}\cdot\texttt{ReLU}\Biggl(\texttt{min}\Bigl(
        1 + \frac{x - B_{i,j}}{B_{i,j} - B_{i, j-1}}\,\,, \quad
        1 - \frac{x - B_{i,j}}{B_{i, j+1} - B_{i,j}}\Bigr)\Biggr)
$$

### Error Estimators
We need error estimators with high effectivity, that is: the ratio of the estimated error to the actual error.

$$
    \eta = \Bigl|\frac{\varepsilon_{\textrm{est}}}{\varepsilon_{\textrm{true}}}\Bigr|
$$

Here, the true error we aim to estimate is the improvement gained from a finer discretization (wider layer).
This could be done by explicitly calculating the finer (wider) solution. However, this is extremely costly 
to do every iteration, more than doubling evaluation time in training. Instead, we currently use finite difference
to approximate the truncation error associated with using a piecewise linear function compared to the next higher
order. If the curvature is too large to be accurately represented by the hat functions, we add a neuron in
$h$-refinement fashion. Similarly, if the curvature is sufficiently small, we may remove a hat function.
