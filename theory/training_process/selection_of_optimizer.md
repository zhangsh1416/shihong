---
title: "Selection of Optimizer in Deep Learning"
layout: single
categories: Training_Process
toc: true
toc_label: "Content"
toc_icon: "file"
toc_sticky: true
---
# Selection of Optimizer in Deep Learning

## Introduction

Choosing the right optimizer is critical in training deep learning models. Optimizers are algorithms that adjust the weights of neural networks to minimize the loss function. Different optimizers have various strategies for updating the model parameters, impacting the speed and efficiency of training.

## Common Optimizers

### 1. Stochastic Gradient Descent (SGD)

**Description:**
- SGD updates the model parameters using the gradient of the loss function with respect to the parameters for a single training example at each iteration.

**Formula:**
<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?\theta_{t+1}=\theta_t-\eta\nabla_{\theta}J(\theta_t;x^{(i)};y^{(i)})" alt="\theta_{t+1}=\theta_t-\eta\nabla_{\theta}J(\theta_t;x^{(i)};y^{(i)})" style="color: #2980B9;" />
</p>
Where:
- <img src="https://latex.codecogs.com/svg.latex?\theta_t" alt="\theta_t" style="color: #2980B9;" />: Model parameters at iteration t
- <img src="https://latex.codecogs.com/svg.latex?\eta" alt="\eta" style="color: #2980B9;" />: Learning rate
- <img src="https://latex.codecogs.com/svg.latex?\nabla_{\theta}J(\theta_t;x^{(i)};y^{(i)})" alt="\nabla_{\theta}J(\theta_t;x^{(i)};y^{(i)})" style="color: #2980B9;" />: Gradient of the loss function with respect to the parameters for a single training example <img src="https://latex.codecogs.com/svg.latex?(x^{(i)},y^{(i)})" alt="(x^{(i)},y^{(i)})" style="color: #2980B9;" />

**Order:**
- First-order optimizer, meaning it uses the first derivative (gradient) of the loss function.

**Advantages:**
- Simple and easy to implement.
- Computationally efficient.

**Disadvantages:**
- High variance in updates can cause the optimization to fluctuate.
- May converge slowly.

**Applications:**
- Suitable for simple or small datasets.
- Often used as a baseline optimizer for comparison with more complex methods.

### 2. SGD with Momentum

**Description:**
- Momentum helps accelerate SGD by dampening oscillations. It accumulates a velocity vector in directions of persistent reduction in the loss function.

**Formula:**
<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?v_t=\gamma{v_{t-1}}+\eta\nabla_{\theta}J(\theta_t)" alt="v_t=\gamma{v_{t-1}}+\eta\nabla_{\theta}J(\theta_t)" />
  <br />
  <img src="https://latex.codecogs.com/svg.latex?\theta_{t+1}=\theta_t-v_t" alt="\theta_{t+1}=\theta_t-v_t" />
</p>
Where:
- <img src="https://latex.codecogs.com/svg.latex?v_t" alt="v_t" style="color: #2980B9;" />: Velocity (momentum) term at iteration t
- <img src="https://latex.codecogs.com/svg.latex?\gamma" alt="\gamma" style="color: #2980B9;" />: Momentum coefficient (typically between 0.5 and 0.9)
- <img src="https://latex.codecogs.com/svg.latex?\eta" alt="\eta" style="color: #2980B9;" />: Learning rate
- <img src="https://latex.codecogs.com/svg.latex?\nabla_{\theta}J(\theta_t)" alt="\nabla_{\theta}J(\theta_t)" style="color: #2980B9;" />: Gradient of the loss function with respect to the parameters at iteration t

**Order:**
- First-order optimizer with momentum, making it effectively utilize past gradients to smooth the optimization path.

**Advantages:**
- Faster convergence compared to plain SGD.
- Reduces oscillations, making the optimization path smoother.

**Disadvantages:**
- Requires tuning of the momentum term.
- May still get stuck in local minima.

**Applications:**
- Effective in training deep neural networks.
- Commonly used in computer vision tasks and image classification problems.

### 3. RMSprop

**Description:**
- RMSprop is designed to resolve AdaGrad's diminishing learning rate problem by using a moving average of squared gradients.

**Formula:**
<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?E[g^2]_t=\gamma{E[g^2]_{t-1}}+(1-\gamma)g_t^2" alt="E[g^2]_t=\gamma{E[g^2]_{t-1}}+(1-\gamma)g_t^2" />
  <br />
  <img src="https://latex.codecogs.com/svg.latex?\theta_{t+1}=\theta_t-\frac{\eta}{\sqrt{E[g^2]_t+\epsilon}}g_t" alt="\theta_{t+1}=\theta_t-\frac{\eta}{\sqrt{E[g^2]_t+\epsilon}}g_t" />
</p>
Where:
- <img src="https://latex.codecogs.com/svg.latex?E[g^2]_t" alt="E[g^2]_t" style="color: #2980B9;" />: Exponential moving average of squared gradients at iteration t
- <img src="https://latex.codecogs.com/svg.latex?\gamma" alt="\gamma" style="color: #2980B9;" />: Decay rate (typically 0.9)
- <img src="https://latex.codecogs.com/svg.latex?g_t" alt="g_t" style="color: #2980B9;" />: Gradient at iteration t
- <img src="https://latex.codecogs.com/svg.latex?\eta" alt="\eta" style="color: #2980B9;" />: Learning rate
- <img src="https://latex.codecogs.com/svg.latex?\epsilon" alt="\epsilon" style="color: #2980B9;" />: Small constant to prevent division by zero

**Order:**
- First-order optimizer with adaptive learning rate adjustment based on past gradients.

**Advantages:**
- Adaptive learning rates for each parameter.
- Prevents learning rate from decaying too quickly.

**Disadvantages:**
- Requires careful tuning of the decay rate.
- Computationally more intensive than plain SGD.

**Applications:**
- Effective for recurrent neural networks (RNNs).
- Commonly used in sequence modeling tasks like language modeling and time-series forecasting.

### 4. Adam (Adaptive Moment Estimation)

**Description:**
- Adam combines the advantages of AdaGrad and RMSprop by keeping an exponentially decaying average of past gradients and squared gradients.

**Formula:**
<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?m_t=\beta_1{m_{t-1}}+(1-\beta_1)g_t" alt="m_t=\beta_1{m_{t-1}}+(1-\beta_1)g_t" />
  <br />
  <img src="https://latex.codecogs.com/svg.latex?v_t=\beta_2{v_{t-1}}+(1-\beta_2)g_t^2" alt="v_t=\beta_2{v_{t-1}}+(1-\beta_2)g_t^2" />
  <br />
  <img src="https://latex.codecogs.com/svg.latex?\hat{m_t}=\frac{m_t}{1-\beta_1^t},\;\hat{v_t}=\frac{v_t}{1-\beta_2^t}" alt="\hat{m_t}=\frac{m_t}{1-\beta_1^t},\;\hat{v_t}=\frac{v_t}{1-\beta_2^t}" />
  <br />
  <img src="https://latex.codecogs.com/svg.latex?\theta_{t+1}=\theta_t-\frac{\eta}{\sqrt{\hat{v_t}}+\epsilon}\hat{m_t}" alt="\theta_{t+1}=\theta_t-\frac{\eta}{\sqrt{\hat{v_t}}+\epsilon}\hat{m_t}" />
</p>
Where:
- <img src="https://latex.codecogs.com/svg.latex?m_t" alt="m_t" style="color: #2980B9;" />: Exponential moving average of the gradient at iteration t
- <img src="https://latex.codecogs.com/svg.latex?v_t" alt="v_t" style="color: #2980B9;" />: Exponential moving average of the squared gradient at iteration t
- <img src="https://latex.codecogs.com/svg.latex?\beta_1,\;\beta_2" alt="\beta_1,\;\beta_2" style="color: #2980B9;" />: Decay rates for the moving averages (typically 0.9 and 0.999, respectively)
- <img src="https://latex.codecogs.com/svg.latex?\hat{m_t},\;\hat{v_t}" alt="\hat{m_t},\;\hat{v_t}" style="color: #2980B9;" />: Bias-corrected estimates
- <img src="https://latex.codecogs.com/svg.latex?\eta" alt="\eta" style="color: #2980B9;" />: Learning rate
- <img src="https://latex.codecogs.com/svg.latex?\epsilon" alt="\epsilon" style="color: #2980B9;" />: Small constant to prevent division by zero

**Order:**
- First-order optimizer with adaptive learning rate adjustment based on both the first and second moments of the gradients.

**Advantages:**
- Combines the benefits of multiple optimizers.
- Suitable for large-scale problems and sparse gradients.
- Adaptive learning rates for each parameter.

**Disadvantages:**
- Requires tuning of multiple hyperparameters.
- Can sometimes lead to poor generalization.

**Applications:**
- Widely used in computer vision and natural language processing tasks.
- Effective for large datasets and complex neural network architectures.

## Comparison of Optimizers

| **Optimizer**           | **Description**                                                                                              | **Order (阶数)** | **Advantages**                                               | **Disadvantages**                                             | **Applications**                                              |
|-------------------------|--------------------------------------------------------------------------------------------------------------|-----------------|--------------------------------------------------------------|---------------------------------------------------------------|----------------------------------------------------------------|
| **SGD**                 | Updates parameters using the gradient of the loss for a single training example                              | First-order     | Simple, computationally efficient                            | High variance in updates, may converge slowly                 | Suitable for simple or small datasets                          |
| **SGD with Momentum**   | Accelerates SGD by adding a velocity term to dampen oscillations                                             | First-order     | Faster convergence, reduces oscillations                     | Requires tuning of momentum term                              | Effective in training deep neural networks                     |
| **RMSprop**             | Uses moving average of squared gradients to normalize learning rate                                          | First-order     | Adaptive learning rates, prevents decay                      | Requires tuning of decay rate                                 | Effective for recurrent neural networks (RNNs)                 |
| **Adam**                | Combines AdaGrad and RMSprop, keeping decaying averages of past gradients and squared gradients               | First-order     | Combines benefits of multiple optimizers, adaptive learning rates | Requires tuning of multiple hyperparameters, may generalize poorly | Widely used in computer vision and NLP tasks                   |

## Summary

The choice of optimizer can significantly impact the training process and performance of deep learning models. Understanding the characteristics and trade-offs of different optimizers is crucial for selecting the right one for your specific application. Common optimizers include SGD, SGD with Momentum, RMSprop, and Adam, each with its own advantages and disadvantages. Selecting the appropriate optimizer involves considering the nature of the problem, the data, and the computational resources available.
