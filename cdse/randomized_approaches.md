---
layout: page
title: Randomized Approaches in Scientific Computing
permalink: /cdse/randomized_approaches
---

### Major Activities 
#### Randomized Inverse Problems
Last year we developed asyptotic convergence analysis for linear inverse problems and numerically 
confirmed the convergence. This year, we extended this analysis to a broad class of nonlinear inverse and 
optimization problems. Additionally, we also proved a non-asymptotic convergence bound for subgaussian random 
variables. Under this unified framework, a variety of existing methods fall out as specializations. 
The beauty of such a framework, however, is that it can be used to uncover new randomization schemes that combine 
the best aspects of existing methods to accelerate both optimization and uncertainty quantification. 
Existing methods that are rediscovered include the randomized MAP method for posterior sampling, 
the randomized misfit approach (left sketching), and the ensemble Kalman filter. 
<!-- We have developed a unified framework under which we can study and understand randomized approaches to solving inverse and other optimization problems.  -->
<!-- We show that various randomized approaches to solving inverse problems can be viewed as special cases of this more general framework.  -->
<!-- In particular, we prove asymptotic and non-asymptotic convergence results for a broad class of randomizations using stochastic optimization theory. -->
<!-- Our unified framework not only recovers many existing methods  -->
<!-- including the randomized MAP method for sampling the posterior, randomized misfit approach (left sketching), and the ensemble kalman filter.  -->
<!-- Additionally, we discover additional methods which combine advantages of existing methods to accelerate both  -->
<!-- optimization and uncertainty quantification. -->
<!-- (including gradient descent, coordinate descent, Karzmarz method, etc) but also discovers new ones. -->

<!---
#### Ensemble Kalman Filter (EnKF) through the lens of duality
The EnKF for inverse problems can be viewed as a special case of the randomized right sketching algorithm. Due to the randomization of the covariance matrix (Regularization) involved, the right sketching algorithm often yields poor results as evident from the Figure below. Therefore, iterative versions of the EnKF is often employed for higher estimation accuracy. We take a new look at the Ensemble Kalman Filter through the lens
of duality. In particular, we show that by dealing with a randomized Lagrangian dual function, the estimation equations as well as asymptotic/non asymptotic convergence results can be derived for the EnKF.  Furthermore, we show that such an interpretation allows one to design improved EnKF algorithms for finding the inverse solution which converges faster.
--->


### Significant Results
We analyze numerically the advantages of sketching the forward map 
from the left compared to sketching from the right and compare results.
For the Shaw problem (*P.C. Hansen, Regularization tools version 4.0*), 
we see that the randomized MAP (Wang, Bui-Thanh, Ghattas) and 
left sketching approaches perform well with few samples while right sketching 
performs poorly. We study this phenomenon from the viewpoint of regularization
and give recommendations on which regularization operators are well-suited for 
use in a right sketching type method. 
![Randomized inverse solutions to Shaw problem](/assets/figures/jon/randomized_IP_shaw.png)

<!-- Some beautiful pictures or videos could go here -->
<!-- [![acoustic-elastic wave equation video](/assets/figures/jon/mangll_animation_frame.png)](/assets/figures/jon/mangll_animation_trimmed.ogv "Mangll video") -->

