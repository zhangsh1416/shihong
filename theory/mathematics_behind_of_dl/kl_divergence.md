---
title: "KL Divergence"
layout: single
categories: Mathematics_Behind_of_DL
toc: true
toc_label: "Content"
toc_icon: "file"
toc_sticky: true      
---
# KL Divergence

## <span style="color: #560E29;">Requirements for KL Divergence</span>

### <span style="color: #27AE60;">Consistent Sample Space:</span>
   - Both distributions P and Q must be defined over the same sample space. This means their domain must be consistent, and they should be comparable within the same sample space.

### <span style="color: #27AE60;">Support Coverage:</span>
   - The support of distribution Q must cover the support of distribution P. In other words, if at any point x, P(x) ≠ 0, then at the same point x, Q(x) must be greater than 0. This ensures that the calculation of KL divergence does not encounter undefined logarithms (log 0).

## <span style="color: #8e44ad;">Calculation Process of KL Divergence</span>

### <span style="color: #16a085;">Discrete Distributions</span>
   - For discrete distributions, the KL divergence is calculated by independently measuring the divergence at each point in the sample space and then summing these values:
     <p align="center" style="color: #2980B9;">
         <img src="https://latex.codecogs.com/svg.latex?D_{KL}(P\|Q)=\sum_xP(x)\log\frac{P(x)}{Q(x)}" alt="D_KL(P||Q)" style="color: #2980B9;" />
     </p>
   - This formula computes the ratio of P(x) and Q(x) at each point x, takes the logarithm of this ratio, multiplies by P(x), and finally sums the results over all points.

### <span style="color: #16a085;">Continuous Distributions</span>
   - For continuous distributions, the calculation is similar but uses integration instead of summation:
     <p align="center" style="color: #2980B9;">
         <img src="https://latex.codecogs.com/svg.latex?D_{KL}(P\|Q)=\int_{-\infty}^{\infty}p(x)\log\frac{p(x)}{q(x)}\,dx" alt="D_KL(P||Q)" style="color: #2980B9;" />
     </p>
   - Here, p(x) and q(x) are the probability density functions of P and Q, respectively. The divergence is integrated over the entire sample space.

## <span style="color: #e67e22;">Summary</span>

The calculation of KL divergence requires a consistent sample space and the support of the approximate distribution to cover the support of the target distribution. The specific calculation involves independently measuring the divergence at each sample point (i.e., taking the ratio of P(x) and Q(x), taking the logarithm, and multiplying by P(x)), then summing these values for discrete cases or integrating for continuous cases. This provides a measure of the difference between two probability distributions.
