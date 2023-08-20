---
layout: page
title: DGGNN
permalink: /nsfOAC/DGGNN/
---
### Discontinuous Galerkin Graph Neural Network model-constrained tangent learning approach for shock-type problems (DG-GNN mcTagent)

Real-time accurate solutions of large-scale complex dynamical systems are in critical need for control, optimization, uncertainty quantification, and decision-making in practical engineering and science applications, especially digital twin applications. Among these, the shock-type problems like Burger equation, Euler equations are far more challenging to solve and train the surrogate models from practical data. In this project, we propose the DG-GNN mcTagent to learn the tangent of the dynamic system of these shock-type problems. Specifically, DG-GNN mcTangent represents a significant advancement over the original mcTangent approach \cite{mcTagent}. It retains the core features of separating temporal and spatial discretizations to capture the method of lines nature. One key enhancement is its ability to handle discontinuous solutions arising from Discontinuous Galerkin (DG) methods. Discontinuous solutions pose challenges in numerical computations, but DG-GNN mcTangent is specifically designed to address these challenges. By leveraging the strengths of the original mc-Tangent approach, DG-GNN mcTangent effectively handles discontinuities, ensuring sufficiently accurate and stable results. Furthermore, DG-GNN mcTangent inherits the localization causality feature of the Graph Neural Network (GNN) architecture. This means it can efficiently capture localized dependencies, benefiting from the GNN’s ability to learn and utilize spatial relationships within the problem domain. This comprehensive framework empowers it to solve dynamical systems with discontinuous solutions while effectively capturing spatial relationships. 

### Results
I have obtained preliminary results for 1D Burger equation and 1D sod tube problem to show the potential of the approach for solving shock-type and discontinuity problems. It can be seen from the figure 1 that DG-GNN mcTangent is able to predict accurately 6 times beyond the training data time horizon. All solutions have excellent agreement with the traditional DG solver solutions. Note that this test data sample case is independently generated from training data. Similar promising results for the 1D sod tube problem are obtained as shown in figure 2. It can be seen that DG-GNN mcTangent learns the propagation of discontinuities as well as the traditional DG solver method.

![Fig1](/assets/figures/hainguyen/DGGNN_fig1.png)

![Fig2](/assets/figures/hainguyen/DGGNN_fig2.png)

