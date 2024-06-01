---
title: "Normalizing Flows"
layout: single
categories: Mathematics_Behind_of_DL
toc: true
toc_label: "Table of Contents"
toc_icon: "file"
toc_sticky: true
---
# Normalizing Flows (NF)

Normalizing Flows (NF) achieve modeling of complex distributions in high-dimensional space without the need to reduce dimensions. This is accomplished by transforming a simple distribution into a complex distribution of the same dimensionality through multiple transformation functions. The probability density at a point in the complex distribution is calculated using the probability density of the simple distribution and the transformation functions.

<h2 style="color: #3498DB;">Key Concepts</h2>

1. **Invertible Transformations**: 
   Each transformation in the NF must be invertible, allowing for the original data to be precisely recovered from the transformed data.

2. **Density Transformation**: 
   Using the transformed data to compute the probability density of the original data, achieved through the Jacobian determinant of the transformation.

3. **Composite Transformations**: 
   Multiple simple transformations are composed together to form a complex transformation flow. Each simple transformation is invertible and has a known Jacobian determinant.

<h2 style="color: #E74C3C;">Mathematical Representation</h2>

Given data <img src="https://latex.codecogs.com/svg.latex?\mathbf{x}" alt="x" style="display:inline-block;"/> , we aim to map it to a simple distribution <img src="https://latex.codecogs.com/svg.latex?\mathbf{z}" alt="z" style="display:inline-block;"/> (usually standard Gaussian) through a series of invertible transformations <img src="https://latex.codecogs.com/svg.latex?f_1, f_2, \ldots, f_K" alt="f1, f2, ..., fK" style="display:inline-block;"/>:

<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?\mathbf{z}=f_K\circ%20f_{K-1}\circ%20\cdots%20f_1(\mathbf{x})" alt="Transformation Function" />
</p>

Since these transformations are invertible, we can map <img src="https://latex.codecogs.com/svg.latex?\mathbf{z}" alt="z" style="display:inline-block;"/> back to the original data space:

<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?\mathbf{x}=f_1^{-1}\circ%20f_2^{-1}\circ%20\cdots%20f_K^{-1}(\mathbf{z})" alt="Inverse Transformation Function" />
</p>

To calculate the probability density of <img src="https://latex.codecogs.com/svg.latex?\mathbf{x}" alt="x" style="display:inline-block;"/>, we use the Jacobian determinant of the transformation:

<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?p(\mathbf{x})=p(\mathbf{z})\left|\det\left(\frac{\partial\mathbf{z}}{\partial\mathbf{x}}\right)\right|^{-1}" alt="Probability Density Calculation" />
</p>

where:

<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?\det\left(\frac{\partial\mathbf{z}}{\partial\mathbf{x}}\right)=\prod_{i=1}^K\left|\det\left(\mathbf{J}_{f_i}\right)\right|" alt="Jacobian Determinant" />
</p>

<h2 style="color: #9B59B6;">Applications</h2>

Normalization flows have several applications, including:

- Generative Models: Generating new data samples similar to the training data.
- Probability Density Estimation: Precisely estimating the probability density of complex data.
- Data Transformation and Preprocessing: Applying complex, non-linear transformations to data for better modeling in data science and machine learning.

<h2 style="color: #1ABC9C;">Combining VAE, VI, and NF</h2>

Variational Autoencoders (VAEs) combine Variational Inference (VI) and Normalizing Flows (NF) to enhance the modeling of latent variables. This combination, known as NF-VAE or Flow-VAE, improves the expressiveness of the latent space.

### Key Points

1. **Dimension Consistency**: Each transformation function <img src="https://latex.codecogs.com/svg.latex?f_i" alt="fi" style="display:inline-block;"/> in NF must have the same input and output dimensions to ensure invertibility.

2. **Invertibility**: The transformation <img src="https://latex.codecogs.com/svg.latex?f_i" alt="fi" style="display:inline-block;"/> must be invertible, with a well-defined inverse transformation <img src="https://latex.codecogs.com/svg.latex?f_i^{-1}" alt="fi inverse" style="display:inline-block;"/>.

3. **Jacobian Determinant**: Computing the Jacobian determinant of the transformation is essential for adjusting the probability density of the transformed data.

### Typical Transformation Functions

- **Affine Coupling Layer**: Applies an affine transformation to part of the input vector while combining it with another part.

  <p align="center" style="color: #2980B9;">
    <img src="https://latex.codecogs.com/svg.latex?\begin{aligned}\mathbf{y}_A&=\mathbf{x}_A\\\mathbf{y}_B&=\mathbf{x}_B\odot\exp(s(\mathbf{x}_A))+t(\mathbf{x}_A)\end{aligned}" alt="Affine Coupling Layer" />
  </p>

- **Element-wise Transformation**: Independent transformation of each element, such as identity or exponential transformations.

- **ActNorm**: Shifts and scales each dimension.

  <p align="center" style="color: #2980B9;">
    <img src="https://latex.codecogs.com/svg.latex?\mathbf{y}=\mathbf{x}\odot\mathbf{s}+\mathbf{b}" alt="ActNorm" />
  </p>

## Conclusion

Normalizing flows provide a powerful method to represent, model, and sample complex high-dimensional distributions without directly reducing dimensionality. They transform the probability density of a simple distribution into that of a complex distribution through a series of invertible transformations, enabling precise modeling and sample generation of complex distributions. This approach is widely used in generative models, probability density estimation, and other machine learning tasks.
