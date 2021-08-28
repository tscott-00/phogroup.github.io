---
layout: page
title: Layerwise DNN Training
permalink: /cdse/layerwise_training
---

### Major Activities 
 Training deep networks suffers from the common problems such as:  i) Need for a gigantic training set to confront over-fitting issue; ii) architecture adaptability problems, e.g., any amendments to a pretrained DNN requires retraining from the scratch. Therefore, there is a need to develop a computationally efficient procedure for training a DNN without making any compromise on the accuracy achieved by traditional back propagation algorithm.

 In this project, we propose a two stage Algorithm for progressively growing neural networks. The first stage is a Layerwise training of neural networks that addresses the issue of the choice of depth of a neural network. Here, the layers are trained one at a time, and once they are trained, the input data are mapped forward through the layer to create a new learning problem. The second stage of the algorithm involves the use of a sequence of small networks to learn important features from error map produced by first stage. We call this as the "additive learning procedure" since the method involves adding up a sequence of networks to determine the final output.



### Significant Results
The proposed framework has been demonstrated on  regression problems such as the Boston housing price prediction problem where the method outperforms a baseline network.

In particular we also demonstrate that the procedure can be used for progressively learning the solutions of PDE. For this purpose, we creatively combine the architecture adaptation procedure with the Physics informed neural network approach. Figure below shows the adaptive approach where one progressively learn the solution of Poisson's equation. 

![image](/assets/figures/Krish/adaptation_1.png)

    Fig 1: Neural architecture adaptation for progressively learning the solution of Poisson's equation

![image2](/assets/figures/Krish/adaptation_2.png)

    Fig 2: Final Neural network solution (on the left) vs True solution (on the right)


