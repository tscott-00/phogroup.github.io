---
layout: page
title: Physics Informed Deep Learning Enhanced by POD
permalink: /nsfcareer/year3/POD
---

### Brief Description

This project focus on forecasting solution of time-dependent PDE’s using a neural network based surrogate model. The first stage in this approach is to perform a POD based model reduction to approximate the system solution. The solution is represented   as a linear combination of orthonormal modes by computing the singular value decomposition of a snapshot matrix. A neural network is then employed to learn the nonlinear map between the POD coefficients, an 'r' dimensional output, and the time instants which are 1 dimensional inputs. However, this approach can only predict solutions within the training data set and fails at forecasting the solutions accurately at a future time instant outside the training data set. In order to deal with this issue, we incorporate a physics term in the loss function, which is the discretized equation for the POD coefficients. Thus the method suitably combines data with physics (governing PDE) to arrive at a good surrogate model for the underlying process. Numerical results on a linear advection equation show that by encoding the physics into the training process, one can forecast the solution accurately at a future time instant.
### Contributors

Jennifer Zheng, Tan Bui-Thanh & C G Krishnanunni

### Report

[Physics Informed Deep Learning Enhanced by POD](/assets/figures/under_graduate_figures/Jennifer.pdf)
