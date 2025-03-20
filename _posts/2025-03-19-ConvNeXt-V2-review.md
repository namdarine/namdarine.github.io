---
layout: post
title: ConvNeXt V2 Paper Review
date: 2025-03-19 18:00:00
description: Paper review
tags: WIS
categories: CV, paper_review
toc:
  sidebar: left
---

> This post summarizes "ConvNeXt V2: Co-designing and Scaling ConvNets with Masked Autoencoders" (Sanghyun Woo et al., CVPR 2023) and shares an implementation based on the ideas presented in the paper. This post was written for learning purposes.

## Abstract & Introduction

ConvNeXt V2 is an improved model of ConvNeXt, a modern convolutional neural network (ConvNet), which significantly improves performance by co-designing self-supervised learning using **Masked Autoencoder (MAE)** and architectural design. Existing ConvNeXt was optimized for supervised learning, but when simply combined with MAE, its performance did not meet expectations.  
To solve this:

1. Fully Convolutional Masked Autoencoder (FCMAE): Transformer-optimized MAE transform to fit ConvNet. It handles masked inputs efficiently by introducing sparse convolution and replacing the decoder with a simple ConvNeXt block to make it a fully convolutional structure.

2. Global Response Normalization (GRN): Add a new normalization layer that enhances feature competition between channels. This solved the feature collapse problem and increased expressiveness.

As a result, ConvNeXt V2 significantly improves the performance of pure ConvNet on various tasks such as ImageNet classification (up to 88.9% accuracy), COCO object detection and ADE20K segmentation. The model is scalable from 3.7M parameter (Atto) to 650M parameter (Huge), and achieves state-of-art performance with public data.

## Core Content Analysis

### Problem definitions and Mathematical modeling

Existing ConvNeXt is well-optimized for supervised learning, but when combined with self-supervised learning, especially MAE, the performance is poor. Since the MAE is designed to be suitable for transformers, it creates compatibility issues with ConvNet's dense sliding window scheme. Furthermore, the expressive power is degraded by "feature collapse" during mask-based pre-training on ConvNet.

### Defined variables and expressions

- **Masking**: Generate a random mask _M_ with 60% mask rate for input image _I_. _M_ is defined in units of $$ 32 \times 32 $$ patches at the last stage and is tailored to the original resolution by upsampling.
- **Sparsal convolution**: Processing only the pixels seen in input $$ X \in \mathbb{R}^{H \times W \times C} $$. Output $$ Y = SparseConv(X, W) $$, where $$ W $$ is learningable filters.
- **GRN**: Global aggregation $$ G(X) = ||X||_{2} $$ for input $$ X \in \mathbb{R}^{H \times W \times C} $$, Normalization $$ N(X) = \frac{X}{G(X)} $$, Correction $$ Y = \gamma \cdot N(X) + \beta $$ ($$ \gamma $$, $$ \beta $$ are learnable parameters).
- **Loss function**: $$ L = MSE(I_{masked}, \hat{I}_{masked}) $$ for masked patches, where $$ \hat{I} $$ is a reconstructed image.

### Assumtion

Suppose that if ConvNet is to be as suitable for mask-based self-supervised learning as Transformer, the architecture, and the learning framework must be co-designed. Assume that the feature collapse comes from a lack of competition between channels.

### Coonection with existing research

MAE has been successful on ViT (HE et al., 2022), but its effectiveness is limited on ConvNet (Jing et al., 2022). ConvNeXt V1 (Liu et al., 2022) has shown scalability in supervised learning, but self-supervised learning has been insufficient.

## Analyzing the suggested methods

### Core Algorithms and Model Structures

- **FCMAE**: Fully convolutional MAE. The encoder applies sparse convolution to ConvNeXt, and the decoder consists of a single ConvNeXt block (512 dimensions). Masked inputs are viewed as sparse data and processed.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/figure2.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
- **GRN**: Normalized layer added behind MLP layer. Global response (L2 norm) increases inter-channel contrast and enhances feature diversity.  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/algorithm1.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
- **ConvNeXt V2**: Integrate GRN into the ConvNeXt block and remove LayerScale. Model size expansion from Atto (3.7M) to Huge (650M).  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/figure5.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
### Improvements over existing research
- MAE (based on ViT) is optimized for transformers with an asymmetric encoder-decoder. FCMAE transforms to full convolution to fit ConvNet, improving efficiency with sparse convolution.  
- SimMIM(based on Swin) and others are transformer-dependent. GRN resolves ConvNet-specific feature collapse and improves performance without additional parameters.  
  
### Originality of the technique
Sparse convolution is inspired by 3D point clouds (Choy et al., 2019), and GRN is an idea from lateral inhibition in neuroscience. Both are newly applied to ConvNet.  
  
## Experimental Interpretations - Key Concept Analysis
### Experimental methods and datasets
#### Used datasets
- **ImageNet-1K**: 1,000 classes, 1.3 million images. 800 epochs of pre-training, 100 epochs of fine-tuning  
- **ImageNet-22K**: 22,000 classes, used for intermediate fine tuning. $ 384 \times 384 $ resolution  
- **COCO**: Object detection and instance segmentation, evaluated with Mask R-CNN  
- **ADE20K**: Semantic segmentation, evaluated with UpperNet  
- **Preprocessing**: Minimum data augmentation (random crop only), patch-wise normalization  
  
#### Experimental environment
- **Hardware**: 256 core TPU-v3 pod (based on JAX)  
- **Software**: PyTorch/JAX, [github](https://github.com/rwightman/pytorch-image-models)  
  
#### Performance comparison indicators
- **ImageNet**: Top-1 accuracy (%)  
- **COCO**: $$ mAP^{box} $$ (detection), $$ mAP^{mask} $$ (segmentation)  
- **ADE20K**: $ mloU $ (Average intersection/union)  
- **Comparative method**: Compare to V1 (supervised), Compare V2 + FCMAE, and Transformer (Swin, ViT)  
  
## Result
### Summary
- ***ImageNet-1K**: V2 + FCMAE is superior to supervised V1 (83.8% and 84.3%) with Base (84.6%), Large (85.6%), and Huge (86.3%). After IN-22K fine-tuning, Huge is 88.9% SOTA  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/table5.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
- **COCO**: V2 + FCMAE Huge is $ mAP^{box} $ 2.5 and $ mAP^{mask} $ 2.0 higher than Swin Huge  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/table6.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
- **ADE20K**: V2 + FCMAE Huge is mIoU 54.0, a significant improvement over supervised V1 (49.9)  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/table7.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
### Reasons for performance improvement
- **FCMAE**: Sparse convolutions prevent information leakage and simple decoders maintain efficiency  
- **GRN**: Improve expressiveness with feature collapse resolution  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/figure3.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/figure4.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
V2 + FCMAE outperforms supervised V2 by 0.8 - 1.3%  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/table3.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
- **co-design**: Synergy between architecture and learning framework achieves transformer-level performance.  
  
## Generality
- Not conditionally dependent: Consistent performance improvement at all sizes, from Atto to Huge  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/figure1.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
- Verify robust transfer learning performance on various tasks (ImageNet, COCO, ADE20K)  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/table6.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/paper1/table7.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
- However, the Huge model may be slightly data-scale dependent, as it has benefited more significantly from the IN-22K additional data
