---
layout: page
title: Autoencoder Compression for Inverse Problems
permalink: /cdse/ae_compression
---
Last year we showed that we were able to use an autoencoder to compress the state solutions of a time-dependent 
PDE, ***u(t)***, significantly saving on storage cost, and then retrieve these solutions by passing the compessed 
state through the decoder portion with high accuracy (5% average relative error). 
For extreme-scale inverse problems, it is not possible to store all of the states in memory at once.
A traditional approach to mitigating this memory constraint is to employ a checkpointing strategy
whereby a select few timesteps are stored and the others discarded. When a discarded timestep is needed, 
it can be recreated by resolving the PDE starting at the nearest previous checkpoint. 
Since solving high dimensional PDEs can be a time consuming task, we propose to use an autoencoder 
approach to compress all timesteps, allowing a representation of the entire state to be stored in memory at once.
When a timestep is needed, the decoder portion of the DNN is used to decompress the timestep. 
This year we showed that such an autoencoder compression strategy is indeed 
a viable alternative to the checkpointing strategy, resulting in inverse solutions that have minimal 
degradation due to perturbations in the state due to compression losses and that the
cost of compression/decompression is lower than the cost of additional solves of the PDE for well-chosen 
neural network architectures.
For a Gauss-Newton optimization method, the compressed states are used in each of the adjoint, incremental forward, 
and incremental adjoint PDE solves, resulting in significant time-savings over the course of solving the inverse problem. 

One particular advantage of this method is that it scales perfectly. The proposed method holds the local (per MPI rank) 
problem size constant and assigns one instance of the autoencoder to each MPI rank with no communication between ranks required 
to compress/decompress. Such a strategy makes this method particularly effective on large problems as the cost of recomputing 
the PDE solution becomes increasingly dominated by communication costs. 

### Significant Results

<p align="center">
<img src="/assets/figures/jon/dense_32_64_surface.png">
<figcaption><b>Figure 1: </b>Relative error of the parameter of interest **Cp** for two different compression levels. The local state size is 4096 and compressed 
size is 32 (left) and 64 (right). This is equivalent to a compression level of 128x and 64x, respectively. The top row shows the 
predicted value of **Cp** and the bottom row shows the relative error. The average relative error is *0.2%* with 128x compression 
and *0.1%* with 64x compression. In this example, there were 64 MPI ranks, leading to a total state size of 262,144. Using GPU, we get 
a 40% speedup over recomputing the forward solution and 20% speedup when using CPU only. These results have been tested and show to hold
parameters with over 16 million DoFs which was run on 4096 processes. </figcaption>
</p>
<!-- ![reconstruction results](/assets/figures/jon/dense_32_64_surface.png) -->



<!-- ![acoustic-elastic state reconstruction](/assets/figures/jon/mangll.gif) -->

<p align="center">
	<img src="/assets/figures/jon/mangll.gif">
	<center><b>Figure 2: </b>Decompressed reconstruction of state matches very closely to original uncompressed state</center>
</p>

<p align="center">
	<img src="/assets/figures/jon/l6_ld_32_cutaway.png">
	<figcaption><b>Figure 3: </b>Primary wave speed reconstruction with cutaway view showing the autoencoder approach correctly identifies the anomaly hidden beneath the surface. This problem shows effectiveness of our proposed algorithm on parameter with 16,777,216 DoFs solved with 4096 CPU cores.</figcaption>
</p>




<!-- ### Major Activities  -->
<!-- Time-dependent PDE constrained inverse problems -->
<!-- are notorious not only for their difficulty in solving, but also for their large memory requirement -->
<!-- --- making it intractable to naively use state-of-the-art -->
<!-- adjoint based techniques. Current approaches to mitigate the intractable memory requirements -->
<!-- use a checkpointing strategy whereby only a small fraction of the state solutions generated -->
<!-- by solving the forward PDE are stored. Checkpointing strategies trade storage for computation -->
<!-- by requiring duplicate solves of the forward PDE during the adjoint phase to recover the -->
<!-- discarded state information. Our approach compresses the state during the forward phase -->
<!-- using the encoding portion of -->
<!-- a pre-trained autoencoder in order to be able to store all of the states in memory --- -->
<!-- eliminating the need for checkpointing and additional PDE solves. The states are then -->
<!-- decompressed as needed during the adjoint phase using the decoder portion of the autoencoder. -->


<!-- ### Significant Results -->

<!-- We have demonstrated that the autoencoder compression algorithm works for states generated by a variety of PDEs including 2D Laplace equation, 2D and 3D acoustic wave equation, and 3D acoustic-elastic wave equation. Shown below is a video comparing the original 3D state of an acoustic-elastic wave equation with the decompressed state using a compression ratio of 64:1. The mean relative error between the two states is 5% over the entire testing dataset. Current results show relative errors ~1e-4 for the inverse solution, but the implementation does not scale well. Ongoing work is being done to improve scalability of the proposed approach.  -->


<!-- <\!-- Some beautiful pictures or videos could go here -\-> -->
<!-- <\!-- [![acoustic-elastic wave equation video](/assets/figures/jon/mangll_animation_frame.png)](/assets/figures/jon/mangll_animation_trimmed.ogv "Mangll video") -\-> -->
<!-- ![acoustic-elastic wave equation video](/assets/figures/jon/mangll.gif) -->

