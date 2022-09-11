---
layout: page
title: A new look at the Ensemble Kalman Filter
permalink: /cdse/kalman
---

 

The field of data assimilation seeks to find the best estimate for the unknown states or parameters in a dynamical system by combining appropriate mathematical models with observations and balancing the uncertainties.  The linear Kalman filter, with extensions and generalizations such as the Extended Kalman filter,  Unscented Kalman filter and Ensemble Kalman filter, has emerged as one of the the most popular data assimilation tool over the past few decades. In particular, the Ensemble Kalman filter (EnKF) has been developed as a recursive filter suitable for state-parameter estimation problems  involving high dimensional PDEs. This project presents new contributions to the derivation and understanding of the Ensemble Kalman filter (EnKF) for inverse problems. Further, we provide a new proof on the convergence of iterative EnKF and show that the new perspective allows one to develop strategies that helps to improve the convergence.  



### Significant Results

The proposed convergence improvement strategy is demonstrated for an Initial Condition Inversion in an Advection-Diffusion Problem. The method is compared with the commonly used additive inflation strategy for convergence improvement and avoiding filter divergence. The results are shown in Figure 1 below. It is clear from Figure 1 that the proposed strategy yields better solution compared to an existing method.



<p align="center">
<img src="/assets/figures/Krish/enkf.png">
<figcaption>Figure 1: a)  Solution obtained by traditional additive inflation strategy; b) True solution; c) Solution obtained by the proposed convergence improvement strategy.</figcaption>
</p>

