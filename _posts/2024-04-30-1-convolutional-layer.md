---
title: "Convolutional Layer"
layout: single
categories: Components_of_NN
permalink: /theory_of_dl/components_of_nn/convolutional_layer
---

## 3.2.2.4. Total Loss

The total loss function is composed of the three losses mentioned above, with the formula:

$$
L_{\text{total}} = L_{\text{pos}} + \lambda_{\text{map}} L_{\text{map}} + \lambda_{\text{laplacian}} L_{\text{laplacian}}
$$

with the weight \( \lambda_{\text{map}} = 10.0 \) and \( \lambda_{\text{laplacian}} = 1.0 \) in this model.

## 3.2.3. Results

In the experiments, the authors test their model of IGCN on the reconstruction work of the human liver. They also compare their results with results from other methods such as P2M (Pixel to Mesh).

![Visual results of IGCN](\_assets\images\logo.jpg)

As shown in the figure below, the IGCN network has better performance in all three metrics used in comparison (MD, RMSE, and DSC), which means the reconstruction of IGCN has better accuracy and similarity to the ground truth. The results are also statistically significant with a p-value less than 0.05.

|           | Initial      | P2M         | IGCN (no mapping) | IGCN         |
|-----------|--------------|-------------|-------------------|--------------|
| **MD [mm]**   | 5.7 ± 2.9    | 5.1 ± 1.5   | 3.9 ± 0.7         | 3.6 ± 1.2    |
| **RMSE [mm]** | 12.1 ± 5.3   | 9.9 ± 5.1   | 9.3 ± 1.8         | 8.4 ± 2.2    |
| **DSC [%]**   | 84.2 ± 7.6   | 86.8 ± 4.0  | 89.4 ± 2.0        | 91.5 ± 3.4   |

_Figure 8: Visual results of IGCN_

