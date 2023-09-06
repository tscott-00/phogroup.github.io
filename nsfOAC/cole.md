---
layout: page
title: B-Functions and Quadrature-Based Neural Networks
permalink: /nsfOAC/cole/
---
### Activation Functions, Universality, and $$\mathcal B_\theta$$ Functions



### Results
Our initial experiments were conducted with the purpose of evaluating this quadrature approximation 
and its convergence to some random function. The figures below depict how the quadrature increases 
in accuracy as the number of quadrature points goes from 10 to 20.

![Quadrature Approximation (N=10)](/assets/figures/breedis/B_Function_Quadrature_Interpolation_10.png)
![Quadrature Approximation (N=20)](/assets/figures/breedis/B_Function_Quadrature_Interpolation_20.png)

By implementing a Neural Network that mimics the quadrature approximations above, we were able to 
better approximate the function with few points, as given in the next figure.

![QBNN Approximation (N=10)](/assets/figures/breedis/BNN_Multiple_Theta_Preds.png)

With a successful implementation of QBNN, current steps involve using QBNN and other standard Neural 
Networks to compare several traditional activation functions using nAI.

