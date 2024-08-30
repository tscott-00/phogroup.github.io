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

Based on two different design philosophies, we have developed two different algorithms:

####  A two-stage strategy for deep neural network architecture adaptation

One of the most promising directions to solving the above problem is perhaps the layerwise training of neural
networks.  Layerwise training of neural networks is an approach that addresses  the issue of the choice of depth of a neural network and the computational complexity involved with training.
In a recent work, we have shown that by equipping a greedy layerwise training approach with  sparsity promoting
regularization and manifold regularization, it is possible to progressively grow a neural network along its depth while achieving superior performance in comparison to a baseline network. We use ``robustness" as a desirable property for deep neural networks and use this as a criteria to devise a two stage strategy (Algo 2.1 and Algo 2.2) for progressively adapting neural network to the given data-set. We demonstrate the approach on a variety of problems such as regression task, classification task, physics informed neural network problem (adaptive PINNs) and adaptive learning of inverse maps from sparse data. A few results on the efficiency of our approach in comparison to other methods is provided below. 



![Fig1](/assets/figures/Krish/result_1.png "fig:summ")

Figure 1 (left) shows the performance of our algorithm on a prototype regression task (Boston house pricing prediction) where we see that our approach outperformed other conventional approaches. Figure 1 (right) shows the performance of our algorithm on the MNIST classification task where again we see that our approach provides the best results.

![Fig2](/assets/figures/Krish/result_2.png "fig:summ2")

![Fig3](/assets/figures/Krish/result_3.png "fig:summ3")

 Figure 2 shows how our approach can be used for a physics informed neural network task. Finally, Figure 3 demonstrates an application of our approach on a regression task characterized by low availability of data. The aim is to learn an inverse map in an adaptive fashion, i.e lean an observable (low dimensional space) to parameter (high dimensional space) map. We show that using the developed procedure, it is possible to impart stability to the learned inverse map thereby improving the prediction accuracy. Figure 3 shows the evolution of parameter (prediction for a given observation data) across the hidden layer. We found that by injecting stability (through manifold regularization) in later layers allows the network to recover fine details in the parameter field when the baseline network fails to do so.  




#### Network topological derivative approach for deep neural architecture adaptation.


In this project, we define the topological derivative for a neural network which is conceptually the derivative of a shape functional with respect to infinitesimal changes in the neural network topology. Using an optimal control viewpoint, we show that the network topological derivative exists under certain conditions and a closed form expression is derived. In particular, we show that computing the network topological derivative involves solving an eigenvalue problem concerning the Hessian of the Hamiltonian with respect to network parameters. The algorithm we derived simply determines the optimal location along the depth where a new layer needs to be introduced during the training phase and the associated parametric initialization for the newly added layer.  We demonstrate our approach on a synthetic data-set generated based on solving the heat equation. Figure 4 shows the relative magnitude of the topological derivative for each layer at different iterations of our alogorithm. Each iteration corresponds to adding a new layer in the network. Comparison with other adaptation strategies showed that our approach provides the best generalization performance (least relative error on a test data-set) as evident from Figure 5. 


![Fig4](/assets/figures/Krish/result_4.png "fig:summ4")

![Fig5](/assets/figures/Krish/result_5.png "fig:summ5")