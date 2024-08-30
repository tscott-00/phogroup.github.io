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

 In the active learning procedure, we need to increase the size of the network as more training data-points are available. For this we use employ the topological derivative approach that we developed last year to make a decision on where to add a new layer and how to initialize the new layer. As an example of how the topological derivative approach works, we provide a sample numerical results for a wind velocity reconstruction problem where the objective is to predict the magnitude of wind velocity on a uniform 3D grid based on sparse measurement data. A brief outline of our procedure is as follows: a) Train a small network (with two hidden
layers and fixed width) for E epochs; b) Compute the topological derivative for each layer by solving an eigen value
problem and identify the optimal location to introduce a new layer along with the corresponding initialization for
the parameters; c) Train the new network with the added layer for E epochs; d) Repeat the steps until there is no
more improvement in the result (decrease in validation loss).


Our sample selection strategy is based on minimizing the variance of an estimator (neural network) which indirectly improves the
generalization (if the bias of the model is small). Note that the variance is a function of the new data-point to be selected.






![Fig4](/assets/figures/Krish/topo.png "fig:summ4")

![Fig5](/assets/figures/Krish/result_5.png "fig:summ5")