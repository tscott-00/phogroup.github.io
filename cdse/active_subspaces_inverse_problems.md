---
layout: page
title: Active Subspaces for Inverse Problems
permalink: /cdse/active_subspaces_inverse_problems
---

<div style="text-align: justify">

### Major Activities 

In the traditional inverse problem, the Tikhonov regularization method is often used, which penalizes equally all data modes. Recently, a few studies show that data-informed directions should be intact. Nevertheless, the important modes are determined by doing an eigendecomposition of the linear operator. Thus, there are two main drawbacks of such a method: (i) it only applies to a linear operator (limited to the linear problem), and (ii) it ignores the observation data. According to this observation, I applied the active subspace method for solving the inverse problem, which can cope with both mentioned issues:
1. This method works for both linear and nonlinear operators. 
2. The active subspace method considers the observation data for detecting the data-informed directions. Then, the regularization is not imposed on these modes. Consequently, this method is robust in terms of regularization parameters.

To begin with, for the linear case, we define the function to determine active subspace

$$ f(x) = \frac{1}{2}\left\| {A} x - d \right\|^2.$$

Then, the active subspace is the first k eigenvectors obtained by decomposition matrix 

$$ C = \int \nabla f(x) \nabla f(x)^T \rho(x) dx  = W \Lambda W^T .$$

The inverse problem equation need to be solved now reads

$$ \min_{x} \frac{1}{2} \left\| {A} W_1 W_1^T x - d \right\|^2 + \frac{1}{2} \left\| {L} x\right\|^2 ,$$

where $$L^T L = I - W_1 W_1^T.$$

For the nonlinear function, the misfit function reads

$$ f(x) = \frac{1}{2}\left\| G(x) - d \right\|^2.$$

The active subspace matrix is derived by Monte-Carlo method

$$ C = \frac{1}{N} \sum_{i = 1}^N \nabla f(x_i) \nabla f(x_i)^T = W \Lambda W^T. $$

The nonlinear inverse probblem is

$$ \min_{x} \, \frac{1}{2}\left\| G(x) - d \right\|^2 + \frac{1}{2}  \left\| {L} \Gamma^{-\frac{1}{2}} x\right\|^2 $$


### Significant Results

1. For the linear inverse problems, the active subspace method allows to get pretty good solution even with only one-dimensional active subspace. However, if we use the traditional manner (i.e. the eigendecomposition of the operator) to determine the data-informed directions, we will be not able to achieve the same accuracy. The reason is that such a convention method does take consideration of data/observation information into dectecting important data modes. The figure 1. shows that, with only one-dimensional active subspace, we are able to catch the main feature of the reconstructed X-Ray image; meanwhile, the traditional data-informed method is not. Table 1. presents the relativ error of the inverse image.

![image](/assets/figures/hainguyen/AS_X_ray_1.png)

![image1](/assets/figures/hainguyen/AS_X_ray_2.png)


2. For the nonlinear inverse problem, while the traditional method is not able to return the data-informed directions, the active subspace method still capable of catching these modes very well. We now consider the poison 2D inverse problem in Hippylib package. 
   
$$ \min_{m} \mathcal{J} := \frac{1}{2} \int_{\Omega} (u - u_d)^2 \, dx + \frac{\gamma}{2} \int_{\Omega} | \nabla m|^2 \, dx, $$ 

where is the solution of

$$ -\nabla \cdot (\exp(m) \nabla u) = f \quad  \text{in} \quad  \Omega$$

associated with boundary conditions

$$ u = 0 \quad  \text{on} \quad  \partial \Omega $$

Without the active subspace, we must pay time to pick properly the regularization parameter, for example, 1e-8 in this problem. Whereas, we can pick more freely from a wide range of parameter, if the active subspace is adapted. The figure 2. shows that the active subspace method allows to get inverse solution with parameter 1e-6.

![image2](/assets/figures/hainguyen/AS_non_linear.png)

