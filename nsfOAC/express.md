---
layout: page
title: Expressivity of Neural Networks
permalink: /nsfOAC/express/
---
### Expressivity of Neural Networks

Neural networks are function approximators whose parameters exist in a very high dimensional space. Because of the layered and strongly inter-connected nature of neural networks, analysis can be difficult. To this end, active subspaces are leveraged as a computational tool for analysis of characteristics of the parameter space for a given neural network. We introduce the concept of a network condition number to measure how easily one can train a given neural network.



### Results

Analysis of the eigendecomposition behavior of a full rank active subspace matrix for the global parameter space has revealed two major findings so far:

- The eigenvalues of the eigendecomposition decay very slowly (on a logarithmic scale), indicating the resistance of the global parameter space to active subspace based dimension reduction techniques.
- The eigenvectors of the eigendecomposition display a discrete structure reflecting the layers of the network, indicating that earlier parameters in the network are more important in that they have a greater effect upon the loss.

<!-- ![The eigenvalues of the active subspace matrix for a network with 5146 parameters and 10000 active subspace samples.](/assets/figures/rusty/CDSE_eigenvalues.png "fig:CDSE_Eigenvalues") -->

<!-- ![The eigenvectors of the active subspace matrix for a network with 5146 parameters and 10000 active subspace samples.](/assets/figures/rusty/CDSE_eigenvectors.png "fig:CDSE_Eigenvectors") -->

Additionally, research has shown that we can create a network "condition number". We see that for various network architectures, the network condition number behaves in a fashion that mimics the behavior of the total parameter count for a network.

![The network condition number for dense fully connected networks evaluated on a sin regression.](/assets/figures/rusty/MTED_plot.png "fig:MTED_plot")

![A contour plot of the total number of parameters for dense fully connected networks.](/assets/figures/rusty/parameter_count_contour.png "fig:parameter_count")

Further analysis is underway to determine the active subspace behavior of model-constrained neural networks.