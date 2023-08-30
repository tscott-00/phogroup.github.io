---
layout: page
title: Neural Architecture Adaptation Problem
permalink: /nsfOAC/adaptation/
---
### Problem description
It has been observed that deep neural networks (DNN) create increasingly
simpler but more useful  representations  of the learning problem layer by layer. Furthermore, empirical
evidence supports the paradigm that depth of a network is of crucial
importance. Such large networks, however, yield
computationally complex optimization problems. Furthermore, despite
such successes, the mechanisms behind deep learning remain a mystery
and a trial-and-error approach (Architecture search) is often employed to retrieve the best
neural network. Thus, there is a need for
adaptive principles to guide the architecture design of a neural network. In this project we focus on developing mathematically principled schemes for progressively adapting neural network to generalize well on the given data set and possibly outperform an adhoc baseline neural network.

### Adopted strategy

Based on two different design philosophies, we have developed two different algorithms:

####  A two-stage strategy for deep neural network architecture adaptation

One of the most promising directions to solving the above problem is perhaps the layerwise training of neural
networks.  Layerwise training of neural networks is an approach that addresses  the issue of the choice of depth of a neural network and the computational complexity involved with training.
In a recent work, we have shown that by equipping a greedy layerwise training approach with  sparsity promoting
regularization and manifold regularization, it is possible to progressively grow a neural network along its depth while achieving superior performance in comparison to a baseline network. We use ``robustness" as a desirable property for deep neural networks and use this as a criteria to devise a two stage strategy for progressively adapting neural network to the given data-set. We demonstrate the approach on a variety of problems such as regression task, classification task, physics informed neural network problem (adaptive PINNs) and adaptive learning of inverse maps from sparse data. A few results on the efficiency of our approach in comparison to other methods is provided below. 



![Left to right: Summary of architecture adaptation results for Boston house price prediction problem: Our approach is the most accurate in comparison to other methods; Summary of adaptation results for MNIST classification proble (20 neurons in each hidden layer): our approach provides the best results with 96.9 % testing accuracy](/assets/figures/Krish/result_1.png "fig:summ")

#### Network topological derivative approach for deep neural architecture adaptation.


In this project, we define the {\it{topological derivative}} for a neural network which is conceptually the derivative of a shape functional with respect to infinitesimal changes in the neural network topology. Using an optimal control viewpoint, we show that the network topological derivative exists under certain conditions and a closed form expression is derived. In particular, we show that computing the network topological derivative involves solving an eigenvalue problem concerning the Hessian of the Hamiltonian with respect to network parameters. The algorithm we derived simply determines the optimal location along the depth where a new layer needs to be introduced during the training phase and the associated parametric initialization for the newly added layer.  