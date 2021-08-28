---
layout: page
title: Neural network expressiveness with active subspaces
permalink: /cdse/active_subspaces_nn_analysis
---

### Major Activities 

Neural networks are function approximators whose parameters exist in a very high dimensional space. Because of the layered and strongly inter-connected nature of neural networks, analysis can be difficult. To this end, active subspaces are leveraged as a computational tool for analysis of characteristics of the parameter space for a given neural network. We introduce the concept of network condition number to measure the network expressiveness.


### Significant Results

The first prominent finding is that all computation units are important.

The following figure illustrates the eigenvalues of the active subspace matrix for a network with 1 input neuron, 1 output neuron, and 5 hidden layers with 35 neurons per hidden layer, giving 5146 parameters total. The active subspace was estimated with ten thousand samples. The losses were calculated on a regression problem to regress a sin function.

![The eigenvalues of the active subspace matrix for a network with 5146 parameters and 10000 active subspace samples.](/assets/figures/rusty/CDSE_eigenvalues.png "fig:CDSE_Eigenvalues")

The second prominent finding is that some network parameters are more important than others, in the sense that the loss is more sensitive to them than others. 

![The eigenvectors of the active subspace matrix for a network with 5146 parameters and 10000 active subspace samples.](/assets/figures/rusty/CDSE_eigenvectors.png "fig:CDSE_Eigenvectors")


<!-- Some beautiful pictures or videos could go here -->
<!-- [![acoustic-elastic wave equation video](/assets/figures/jon/mangll_animation_frame.png)](/assets/figures/jon/mangll_animation_trimmed.ogv "Mangll video") -->

