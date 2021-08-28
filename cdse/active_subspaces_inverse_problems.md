---
layout: page
title: Active Subspace Data-Informed Inversion Method
permalink: /cdse/active_subspaces_inverse_problems
---

### Major Activities 

In the traditional inverse problem, the Tikhonov regularization method is often used, which penalizes equally all data modes. Recently, a few studies show that data-informed directions should be intact. Nevertheless, the important modes are determined using an eigendecomposition of the linear operator. There are two main drawbacks of such a method: (i) it only applies to a linear operator (limited to the linear problem), and (ii) it ignores observational data. In order to address these two issues we have developed an active subspace data-informed inversion approach. In particular, our method works for both linear and nonlinear operators. 

### Significant Results

#### Linear inverse problem (X-Ray imaging)

As can be seen in the Figure 1 below, our approach provides a reasonable solution even with only one active vector. 
Indeed, the solution is able to reconstruct the main feature of the X-Ray image, while the traditional data-informed method is not. Table 1. presents the relative error of the inverse image.

![image](/assets/figures/hainguyen/AS_X_ray_1.png)

![image1](/assets/figures/hainguyen/AS_X_ray_2.png)


#### Nonlinear PDE-constrained inverse problem

We now consider the poison 2D inverse problem in Hippylib package. 
   
$$ \min_{m} \mathcal{J} := \frac{1}{2} \int_{\Omega} (u - u_d)^2 \, dx + \frac{\gamma}{2} \int_{\Omega} | \nabla m|^2 \, dx, $$ 

where $ u$ is the solution of the following PDE

$$ -\nabla \cdot (\exp(m) \nabla u) = f \quad  \text{in} \quad  \Omega$$

with boundary conditions

$$ u = 0 \quad  \text{on} \quad  \partial \Omega $$

<!---
Without the active subspace, we must take time to tune properly the regularization parameter, for example, 1e-8 in this problem. Whereas, we can pick more freely from a wide range of parameter when the active subspace mmethod is adapted. The figure 2. shows that the active subspace method allows to get inverse solution with parameter 1e-6.
--->
Fig 2 shows that our active subspace data-informed approach outperforms the traditional Tikhonov inversion method.

![image2](/assets/figures/hainguyen/AS_non_linear.png)

