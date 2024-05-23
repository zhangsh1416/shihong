---
title: "Distribution Metrics"
layout: single
categories: Common_Issues
---
# KL Divergence and FID
## KL Divergence (Kullback-Leibler Divergence)

<span style="color: #2980B9;">***Definition***</span>: *KL Divergence is a measure of how one probability distribution diverges from a second, expected probability distribution.*

<span style="color: #2980B9;">***Mathematical Formula***</span>:

<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?D_{KL}(P\parallel Q)=\sum_{i}P(i)\log\frac{P(i)}{Q(i)}" alt="KL Divergence Formula" style="color: #2980B9;" />
</p>

or in the continuous case:

<p align="center" style="color: #2980B9;">
  <img src="https://latex.codecogs.com/svg.latex?D_{KL}(P\parallel Q)=\int P(x)\log\frac{P(x)}{Q(x)}dx" alt="Continuous KL Divergence Formula" style="color: #2980B9;" />
</p>

<span style="color: #2980B9;">***Characteristics***</span>:
- ***Non-symmetric***: <img src="https://latex.codecogs.com/svg.latex?D_{KL}(P\parallel Q)\neq D_{KL}(Q\parallel P)" alt="Non-symmetric" style="color: #2980B9;" />
- ***Non-negative***: Always non-negative and zero if and only if <img src="https://latex.codecogs.com/svg.latex?P=Q" alt="Non-negative" style="color: #2980B9;" />
- ***Sensitive to the support of*** \( Q \): If <img src="https://latex.codecogs.com/svg.latex?Q(i)=0" alt="Sensitive to Support" style="color: #2980B9;" /> and <img src="https://latex.codecogs.com/svg.latex?P(i)>0" alt="Sensitive to Support" style="color: #2980B9;" />, KL Divergence goes to infinity.
- ***Measures relative entropy***: Quantifies the amount of information lost when <img src="https://latex.codecogs.com/svg.latex?Q" alt="Q" style="color: #2980B9;" /> is used to approximate <img src="https://latex.codecogs.com/svg.latex?P" alt="P" style="color: #2980B9;" />.

<span style="color: #2980B9;">***Uses***</span>:
- ***Model evaluation***: Comparing theoretical distributions with empirical distributions.
- ***Information theory***: Quantifying information gain in Bayesian updating.
- ***Optimization***: Often used in the training of machine learning models, such as in Variational Autoencoders (VAEs).

## FID (Frechet Inception Distance)

<span style="color: #E67E22;">***Definition***</span>: *FID measures the distance between two distributions of images by comparing their feature representations obtained from a pre-trained network (typically Inception-v3).*

<span style="color: #E67E22;">***Mathematical Formula***</span>:

<p align="center" style="color: #E67E22;">
  <img src="https://latex.codecogs.com/svg.latex?\text{FID}(P_r,P_g)=\|\mu_r-\mu_g\|^2+\text{Tr}(\Sigma_r+\Sigma_g-2(\Sigma_r\Sigma_g)^{1/2})" alt="FID Formula" style="color: #E67E22;" />
</p>

where <img src="https://latex.codecogs.com/svg.latex?(\mu_r,\Sigma_r)" alt="Mean and Covariance" style="color: #E67E22;" /> and <img src="https://latex.codecogs.com/svg.latex?(\mu_g,\Sigma_g)" alt="Mean and Covariance" style="color: #E67E22;" /> are the mean and covariance of real and generated image features, respectively.

<span style="color: #E67E22;">***Characteristics***</span>:
- ***Symmetric***: <img src="https://latex.codecogs.com/svg.latex?\text{FID}(P,Q)=\text{FID}(Q,P)" alt="Symmetric" style="color: #E67E22;" />
- ***Robust***: More robust to noise and minor variations in the data.
- ***Sensitive to both quality and diversity***: Captures discrepancies in both the mean and the spread of feature distributions.
- ***Uses pre-trained model***: Relies on Inception-v3 for feature extraction, providing a standardized comparison.

<span style="color: #E67E22;">***Uses***</span>:
- ***GAN evaluation***: Widely used to evaluate the performance of Generative Adversarial Networks.
- ***Image synthesis***: Measuring the quality and diversity of generated images.
- ***Model comparison***: Comparing different generative models or different training strategies.

# Comparison Table

| Feature                      | <span style="color: #2980B9;">KL Divergence</span>                              | <span style="color: #E67E22;">FID (Frechet Inception Distance)</span>             |
|------------------------------|--------------------------------------------|---------------------------------------------|
| ***Symmetry***               | <span style="color: #2980B9;">Non-symmetric</span>                              | <span style="color: #E67E22;">Symmetric</span>                                   |
| ***Sensitivity to Support*** | <span style="color: #2980B9;">Highly sensitive to zero probabilities</span>     | <span style="color: #E67E22;">Robust to support mismatches</span>                |
| ***Measures***               | <span style="color: #2980B9;">Relative entropy</span>                           | <span style="color: #E67E22;">Distance in feature space</span>                   |
| ***Application Domain***     | <span style="color: #2980B9;">Information theory, model optimization</span>     | <span style="color: #E67E22;">Generative model evaluation</span>                 |
| ***Computation***            | <span style="color: #2980B9;">Direct probability comparison</span>              | <span style="color: #E67E22;">Feature-based comparison using pre-trained model</span> |
| ***Typical Uses***           | <span style="color: #2980B9;">Variational Autoencoders, Bayesian methods</span> | <span style="color: #E67E22;">GAN evaluation, image quality assessment</span>    |
| ***Robustness***             | <span style="color: #2980B9;">Can be unstable with non-overlapping supports</span> | <span style="color: #E67E22;">Robust to noise and minor variations</span>       |
| ***Quality vs Diversity***   | <span style="color: #2980B9;">Less effective in capturing diversity</span>      | <span style="color: #E67E22;">Captures both quality and diversity</span>         |

# Conclusion

KL Divergence and FID are both valuable metrics but serve different purposes. KL Divergence is primarily used in theoretical contexts and model optimization tasks where direct probability comparisons are feasible. FID, on the other hand, is tailored for evaluating generative models, especially in terms of image quality and diversity, and is more robust and symmetric, making it a preferred choice in practical applications involving image synthesis and generative models.
