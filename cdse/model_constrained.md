---
layout: page
title: Model Constrained DNNs for Inverse Problems
permalink: /cdse/model_constrained
---

<!-- <div style="text-align: justify"> -->

### Major Activities

In this project, we introduce several model-constrained approaches—including both feed-forward deep neural network (DNN) and autoencoders—that are capable of learning not only information hidden in the training data but also in the underlying mathematical models to solve inverse problems.  We present and provide intuitions for our formulations for general nonlinear problems.   For linear inverse problems and linear networks,  the first-order optimality conditions show that our model-constrained deep learning (mcDL) approaches can learn information encoded in the underlying mathematical models and thus can produce consistent or equivalent inverse solutions.

### Specific Objectives

The main idea is that we take advantage of the forward map G for regularizing the network. Moreover, we also expect that it is consistent with the form of the inverse solution; and thus, improving the accuracy of the training test. To have some intitutions of the method, let us look at the case of linear network and linear inverse problem with linear operator. The formulation of mcDNN approach is

$$ \min_{\textbf{b},W} \frac{1}{2} \left\| U - (WY + B) \right\|_{\Gamma^{-1}}^2 +\frac{\alpha}{2} \left\|  Y -G (WY + B)\right\|_{\Lambda^{-1}}^2.$$

The optimal solution of the DNN training problem satisfies

$$ \textbf{b} = (\Gamma^{-1} + \alpha G^T \Lambda^{-1} G)^{-1} (\Gamma^{-1} \bar{\textbf{u}} + \alpha G^T \Lambda^{-1}  \bar{\textbf{y}} - {\Gamma^{-1} \bar{U} \, \bar{Y}^{\dagger} + \alpha G^T \Lambda^{-1} \bar{Y} \, \bar{Y}^{\dagger}} \bar{\textbf{y}}), $$

$$ W = (\Gamma^{-1} + \alpha G^T \Lambda^{-1} G)^{-1}  (\Gamma^{-1} \bar{U} \,\bar{Y}^{\dagger} + \alpha G^T \Lambda^{-1}\bar{Y} \, \bar{Y}^{\dagger}). $$

Thus, for a given testing/observational data, the mcDNN inverse solution is given by

$$ \textbf{u}_{\text{mcDNN}} = (\Gamma^{-1} + \alpha G^T \Lambda^{-1} G)^{-1}   (\Gamma^{-1} \bar{\textbf{u}} + \alpha G^T \Lambda^{-1} \bar{\textbf{y}} + (\Gamma^{-1} \bar{U} \, \bar{Y}^{\dagger} + \alpha G^T \Lambda^{-1} \bar{Y} \, \bar{Y}^{\dagger}) (\textbf{y}_{\text{obs}} - \bar{\textbf{y}})) $$

which is exactly the solution of the following regularized linear inverse problem

$$
\min_{\textbf{u}} \frac{1}{2}  \left\|\textbf{y}_{\text{obs}} - G \textbf{u}\right\|_{\Gamma^{-1}}^2 + \frac{1}{2\alpha} \left\|\textbf{u} - \textbf{u}_0 \right\|_{\Lambda^{-1}}^2,
$$

where

$$
\textbf{u}_0 =  \bar{\textbf{u}} +\bar{U} \, \bar{Y}^{\dagger} (\textbf{y}_{\text{obs}} - \bar{\textbf{y}}) - \alpha \Gamma G^T \Lambda (I - \bar{Y} \, \bar{Y}^{\dagger}) (\textbf{y}_{\text{obs}} - \bar{\textbf{y}}).
$$


### Significant Results

The results for the linear inverse problem with a linear neural network show that the model-constrained term added to the cost function gives better results than the purely navie DNN. In particular, the accuracy of pure NN solely depends on how much training data we have. Meanwhile, with the same training data set, the mcDNN approach gives a lower error in the test data set since that lowest error point coincides with the optimal regularization parameter of the inverse problem solver. Briefly, in the mcDNN approach, the forward map term parameter almost corresponds to the regularization parameter in the inverse linear problem.

![image1](/assets/figures/hainguyen/mcDNN_fig_1.png "fig:")
![image2](/assets/figures/hainguyen/mcDNN_fig_2.png "fig:")

More detail about this work can be found at https://arxiv.org/abs/2105.12033.
