---
layout: page
title: DIAS: A Model-Constrained Tangent Manifold Learning Approach for Dynamical Systems
permalink: /cdse/mctangent
---

### Major Activities 
This work has been completed during this year and is under rereview in International Journal of Computational Fluid Dynamics. The abtract: Real-time accurate solutions of large-scale complex dynamical systems are in critical
need for control, optimization, uncertainty quantification, and decision-making in practical engineering and science applications. This paper contributes in this direction a model-constrained tangent
manifold learning (mcTangent) approach. At the heart of mcTangent is the synergy of several desirable strategies: i) a tangent manifold learning to take advantage of the neural network speed and
the time-accurate nature of the method of lines; ii) a model-constrained approach to encode the
neural network tangent with the underlying governing equations; iii) sequential learning strategies to
promote long-time stability and accuracy; and iv) data randomization approach to implicitly enforce
the smoothness of the neural network tangent and its likeliness to the truth tangent up second order
derivatives in order to further enhance the stability and accuracy of mcTangent solutions. Both semiheuristic and rigorous arguments are provided to analyze and justify the proposed approach. Several
numerical results for transport equation, viscous Burger’s equation, and Navier-Stokes equation are
presented to study and demonstrate the capability of the proposed mcTangent learning approach.

<p align="center">
<img src="/assets/figures/hainguyen/mctangent_0.png">
<figcaption><b>Figure 1:</b> The schematic of mcTangent network architecture for S = 1.</figcaption>
</p>

### Significant Results


<p align="center">
<img src="/assets/figures/hainguyen/mctangent_1.png">
<figcaption><b>Figure 2:  Wave/transport equation.</b> Trained model-constrained linear neural network weight matrices with model-constrained regularization α = 1e5, noise level δ = 1%. S is number of sequential training steps, R is number of sequential model-constrained steps. The model-constrained weight matrices, after ignoring small elements, have the same structure as the first-order upwind scheme matrix.</figcaption>
</p>



<p align="center">
<img src="/assets/figures/hainguyen/mctangent_3.gif">
<figcaption><b>Figure 3: : Burger’s equations.</b> The solutions of Burgers equation obtained by Finite different method versus mctangent learning approach versus pure machine learning approach.</figcaption>
</p>


<p align="center">
<img src="/assets/figures/hainguyen/mctangent_4.png">
<figcaption><b>Figure 4: : Burger’s equations.</b> Predicted solutions at different times obtained by Backward Euler (BE) scheme using large stepsize
∆t' = 12.5∆t = 1.25 × 10−2 with the true tangent manifold (True map) and the learned one (Learned map).</figcaption>
</p>


<p align="center">
<img src="/assets/figures/hainguyen/mctangent_2.png">
<figcaption><b>Figure 5: Navier-Stokes equation.</b> Comparison of various neural network solutions. Top row: Spectral method (Crank–Nicolson time integration scheme) with the true tangent manifold; Second row: Forward Euler (FE) scheme (a different scale bar in the third and fourth columns); Third row: Backward Euler (BE) scheme with the learned neural network for 20 times larger time stepsize ∆t' = 20∆t.</figcaption>
</p>



<!-- 
<p align="center">
<img src="/assets/figures/hainguyen/...">
<figcaption><b>Figure 1: </b> ... </figcaption>
</p>

 -->






