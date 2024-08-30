---
layout: page
title: Neural Architecture Adaptation Problem
permalink: /nsfOAC/adaptation/
---
### Problem description
Last year, we developed and demonstrated two adaptive principles to guide the architecture design of a neural
network. In particular, our framework for adaptivity  involves computing a quantity
called as the “**topological derivative**” which finds enormous application in the field of structural mechanics, image
processing and inverse problems. This year we also explored several potential applications
of the “topological derivative” especially in the context of **active learning**. The problem statement can be summarized as follows:

- Conventional active learning (adaptive data sampling) strategies start by training on a few labeled data
samples. In order to confront the overfitting of a small dataset, it is essential to choose a small neural
network in the beginning. However, as new data points are queried and added to the training data set, it is
essential to increase the capacity of the network to improve the generalization. Therefore, it is essential to
develop an active learning framework that incorporates architecture adaptation.
- A well-known issue in statistical active learning literature is the training saturation problem, i.e tendency
to get trapped in a local minima and unable to learn on augmenting the training dataset with a new datapoint. It is imperative to have a strategy that handles this issue.


### Adopted strategy

In this work we develop a new active learning strategy that incorporates neural
network architecture adaptation in the framework. In particular, we provide answers to the following questions:

- When to add a new layer during the active learning procedure?

- Where (at which position along the depth) to add a new layer and how to initialize this newly added layer?

- How does adding a new layer influence the query selection strategy?

- How to solve the sample saturation and training saturation problem in statistical active learning framework?

#### Brief outline of the proposed approach


In this project, we define the topological derivative for a neural network which is conceptually the derivative of a shape functional with respect to infinitesimal changes in the neural network topology. Using an optimal control viewpoint, we show that the network topological derivative exists under certain conditions and a closed form expression is derived. In particular, we show that computing the network topological derivative involves solving an eigenvalue problem concerning the Hessian of the Hamiltonian with respect to network parameters. The algorithm we derived simply determines the optimal location along the depth where a new layer needs to be introduced during the training phase and the associated parametric initialization for the newly added layer.  We demonstrate our approach on a synthetic data-set generated based on solving the heat equation. Figure 4 shows the relative magnitude of the topological derivative for each layer at different iterations of our alogorithm. Each iteration corresponds to adding a new layer in the network. Comparison with other adaptation strategies showed that our approach provides the best generalization performance (least relative error on a test data-set) as evident from Figure 5. 


![Fig4](/assets/figures/Krish/result_4.png "fig:summ4")

![Fig5](/assets/figures/Krish/result_5.png "fig:summ5")