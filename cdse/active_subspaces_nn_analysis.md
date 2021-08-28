---
layout: page
title: Neural network expressiveness with active subspaces
permalink: /cdse/active_subspaces_nn_analysis
---

### Major Activities 

Neural networks are function approximators whose parameters exist in a very high dimensional space. Because of the layered and strongly inter-connected nature of neural networks, analysis can be difficult. To this end, active subspaces are leveraged as a computational tool for analysis of characteristics of the parameter space for a given neural network. We introduce the concept of network condition number to measure the network expressiveness.

<!---

In order to train a network, we need a loss $$f(x)$$ function. We must also assume a prior distribution for network parameters to sample from; in this case, the standard normal probability distribution $$\rho(x)$$. Using these we can define the active subspace matrix

$$ C = \int \nabla f(x) \nabla f(x)^T \rho(x) d x = W \Lambda W^T. $$

This analytical expression is approximated via Monte Carlo by performing the following

$$ C \approx \frac{1}{N} \sum_{j=1}^N \nabla f_j \nabla f_j^T = \hat W \hat \Lambda \hat W^T. $$

The gradients of the loss are computed with respect to the network parameters.

We leverage the eigendecomposition of the covariance matrix $$C$$ for our computational analysis.
--->

### Significant Results

The first prominent finding is that the eigenvalues of the eigendecomposition of the active subspace matrix for the global parameter space decay very slowly. This indicates a strong resistance of neural networks to active-subspace-based global dimension reduction techniques.

The following figure illustrates the eigenvalues of the active subspace matrix for a network with 1 input neuron, 1 output neuron, and 5 hidden layers with 35 neurons per hidden layer, giving 5146 parameters total. The active subspace was estimated with ten thousand samples. The losses were calculated on a regression problem to regress a sin function.

![The eigenvalues of the active subspace matrix for a network with 5146 parameters and 10000 active subspace samples.](/assets/figures/rusty/CDSE_eigenvalues.png "fig:CDSE_Eigenvalues")

The second prominent finding is that some network parameters are more important than others, in the sense that the loss is more sensitive to them than others. Because the eigendecomposition is computed via a snapshot SVD of the gradient matrix $$\nabla F$$, the eigendecomposition is ordered. This means the eigenvectors, which are precisely the left singular vectors, are also ordered. Therefore further "right" along the columns of $$\hat W$$ (or the larger the index of the eigenvector), the less important the eigenvector.

Furthermore, we recognize that a transformation $$A x = b$$ can be interpreted such that $$b$$ is just a linear combination of the column vectors of $$A$$. We apply similar logic to the transformation $$y = \hat W^T x$$, where the row vectors of $$\hat W^T$$ are the eigenvectors and where $$x$$ is the vector of network parameters. Because each element of a row of $$\hat W^T$$ corresponds to a parameter in the original space and because $$\hat W$$ is unitary, we can look at the magnitudes of the components of the eigenvectors to determine which parameters have a greater impact on the active subspace transformation, and by extension, the network loss.

![The eigenvectors of the active subspace matrix for a network with 5146 parameters and 10000 active subspace samples.](/assets/figures/rusty/CDSE_eigenvectors.png "fig:CDSE_Eigenvectors")

This plot contains the base-10 log of the absolute value of the eigenvectors in $$\hat W$$ ; the eigenvectors are columns and the rows correspond to parameters in the original parameter space. The dominant eigenvectors are on the left, and the further right one travels along the plot, the less important the eigenvectors.

From this figure we can see that the dominant eigenvectors have larger coefficients corresponding to the parameters mapping from the input layer to the first hidden layer, and from the final hidden layer to the output layer. Because the active subspace matrix is the covariance of the loss gradient with respect to network parameters, this means the network loss is most sensitive to the aforementioned parameters. Note that the horizontal striations in the eigenvector plot corresponds to the connections between hidden layers.

The third and final prominent finding is that in order to reliably estimate the eigendecomposition of the active subspace matrix, there needs to be at least as many samples used to estimate the active subspace as there are network parameters.



<!-- Some beautiful pictures or videos could go here -->
<!-- [![acoustic-elastic wave equation video](/assets/figures/jon/mangll_animation_frame.png)](/assets/figures/jon/mangll_animation_trimmed.ogv "Mangll video") -->

