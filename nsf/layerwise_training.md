---
layout: page
title: New approach for DNN architecture design
permalink: /nsf/layerwise_training.md
---

### Major Activities 
 Training deep networks suffers from the common problems such as:  i) Need for a gigantic training set to confront over-fitting issue; ii) architecture adaptability problems, e.g., any amendments to a pretrained DNN requires retraining from the scratch. Therefore, there is a need to develop a computationally efficient procedure for training a DNN without making any compromise on the accuracy achieved by traditional back propagation algorithm.

 In this project, we propose a two stage Algorithm for progressively growing neural networks.



### Significant Results
The proposed framework has been demonstrated on  regression problems such as the Boston housing price prediction problem where the method outperforms a baseline network.

In particular we also demonstrate that the procedure can be used for progressively learning the solutions of PDE. Figure below shows the adaptive approach where one progressively learn the solution of Poisson's equation. 

![image](/assets/figures/Krish/adaptation_1.png)

    Fig 1: Neural architecture adaptation for progressively learning the solution of Poisson's equation

![image2](/assets/figures/Krish/adaptation_2.png)

    Fig 2: Final Neural network solution (on the left) vs True solution (on the right)


