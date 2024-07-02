---
title: "Fully Connected Layer in Deep Learning"
layout: single
categories: Components_of_NN
toc: true
toc_label: "Content"
toc_icon: "file"
toc_sticky: true      
---
# Fully Connected Layer in Deep Learning

## Detailed Explanation of Fully Connected Layer

A fully connected layer, also known as a dense layer, is a fundamental component of neural networks where each neuron is connected to every neuron in the previous and subsequent layers. This layer is typically used at the end of a network to combine features learned by convolutional layers or recurrent layers into final outputs like classification or regression results.

### How Fully Connected Layer Works

1. **Input and Weights:** Each input neuron is connected to each output neuron via a weight. These weights are learned during training.
   <p align="center" style="color: #2980B9;">
     <img src="https://latex.codecogs.com/svg.latex?y_i=\sum_{j}w_{ij}x_j+b_i" alt="y_i=\sum_{j}w_{ij}x_j+b_i" style="color: #2980B9;" />
   </p>
   Here, <img src="https://latex.codecogs.com/svg.latex?y_i" alt="y_i" style="color: #2980B9;" /> is the output, <img src="https://latex.codecogs.com/svg.latex?w_{ij}" alt="w_{ij}" style="color: #2980B9;" /> are the weights, <img src="https://latex.codecogs.com/svg.latex?x_j" alt="x_j" style="color: #2980B9;" /> are the inputs, and <img src="https://latex.codecogs.com/svg.latex?b_i" alt="b_i" style="color: #2980B9;" /> are the biases.

2. **Activation Function:** After computing the weighted sum, an activation function is applied to introduce non-linearity.
   <p align="center" style="color: #2980B9;">
     <img src="https://latex.codecogs.com/svg.latex?a_i=f(y_i)" alt="a_i=f(y_i)" style="color: #2980B9;" />
   </p>
   Here, <img src="https://latex.codecogs.com/svg.latex?a_i" alt="a_i" style="color: #2980B9;" /> is the activation and <img src="https://latex.codecogs.com/svg.latex?f" alt="f" style="color: #2980B9;" /> is the activation function.

3. **Output:** The final output is a transformed version of the input, passing through the fully connected layer and its activation function.

### Properties and Advantages

- **Global Connectivity:** Each neuron in the layer is connected to every neuron in the previous layer, allowing for integration of all input features.
- **Flexibility:** Can model complex functions due to its dense connections.
- **Feature Combination:** Combines features from previous layers to make final predictions.

### Uses

- **Final Layers in Networks:** Commonly used at the end of CNNs and RNNs for classification or regression.
- **Feature Integration:** Aggregates learned features for decision-making.

## Comparison of Fully Connected Layer Parameters

| **Parameter**  | **Description**                                              | **Impact**                                                                                                  |
|----------------|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| **Weights**    | Parameters connecting inputs to outputs                      | Number of weights increases with number of neurons, leading to higher computational and memory demands      |
| **Biases**     | Additional parameters added to the weighted sum              | Adds flexibility to the model by allowing the activation threshold to shift                                 |
| **Activation** | Function applied to the weighted sum output                  | Introduces non-linearity, enabling the model to learn complex patterns                                      |

### Example of Fully Connected Layer Operation

Consider a fully connected layer with 3 inputs and 2 outputs:

1. **Inputs:** <img src="https://latex.codecogs.com/svg.latex?\mathbf{x}=\begin{bmatrix}x_1 \\ x_2 \\ x_3 \end{bmatrix}" alt="\mathbf{x}=\begin{bmatrix}x_1 \\ x_2 \\ x_3 \end{bmatrix}" style="color: #2980B9;" />
2. **Weights:** <img src="https://latex.codecogs.com/svg.latex?\mathbf{W}=\begin{bmatrix}w_{11} & w_{12} & w_{13} \\ w_{21} & w_{22} & w_{23} \end{bmatrix}" alt="\mathbf{W}=\begin{bmatrix}w_{11} & w_{12} & w_{13} \\ w_{21} & w_{22} & w_{23} \end{bmatrix}" style="color: #2980B9;" />
3. **Biases:** <img src="https://latex.codecogs.com/svg.latex?\mathbf{b}=\begin{bmatrix}b_1 \\ b_2 \end{bmatrix}" alt="\mathbf{b}=\begin{bmatrix}b_1 \\ b_2 \end{bmatrix}" style="color: #2980B9;" />

The output is computed as:
<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?\mathbf{y}=\mathbf{W}\mathbf{x}+\mathbf{b}" alt="\mathbf{y}=\mathbf{W}\mathbf{x}+\mathbf{b}" style="color: #2980B9;" />
</p>
which gives:
<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?\begin{bmatrix}y_1 \\ y_2 \end{bmatrix} = \begin{bmatrix}w_{11} & w_{12} & w_{13} \\ w_{21} & w_{22} & w_{23} \end{bmatrix} \begin{bmatrix}x_1 \\ x_2 \\ x_3 \end{bmatrix} + \begin{bmatrix}b_1 \\ b_2 \end{bmatrix}" alt="\begin{bmatrix}y_1 \\ y_2 \end{bmatrix} = \begin{bmatrix}w_{11} & w_{12} & w_{13} \\ w_{21} & w_{22} & w_{23} \end{bmatrix} \begin{bmatrix}x_1 \\ x_2 \\ x_3 \end{bmatrix} + \begin{bmatrix}b_1 \\ b_2 \end{bmatrix}" style="color: #2980B9;" />
</p>

After applying the activation function, the final output is:
<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?\mathbf{a}=f(\mathbf{y})" alt="\mathbf{a}=f(\mathbf{y})" style="color: #2980B9;" />
</p>
