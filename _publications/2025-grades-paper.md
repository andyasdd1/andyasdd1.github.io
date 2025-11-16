---
title: "GradES: Significantly Faster Training in Transformers with Gradient-Based Early Stopping"
collection: publications
category: conferences
permalink: /publication/2025-grades
excerpt: 'A novel gradient-based early stopping method that operates at the component level within transformer architectures, achieving 1.57x to 7.22x training speedup while improving model generalization.'
date: 2025-09-01
venue: 'arXiv preprint'
paperurl: 'https://arxiv.org/abs/2509.01842'
citation: 'Qifu Wen, Xi Zeng, Zihan Zhou, Shuaijun Liu, Mehdi Hosseinzadeh, Ningxin Su, Reza Rawassizadeh. &quot;GradES: Significantly Faster Training in Transformers with Gradient-Based Early Stopping.&quot; <i>arXiv preprint arXiv:2509.01842</i>, 2025.'
header:
  teaser: grades-architecture.png
---

## Abstract

The paper introduces GradES, a novel gradient-based early stopping method that operates at the component level within transformer architectures (attention projections and Feed-Forward layers). It addresses the high computational cost of traditional early stopping, which relies on global validation loss. GradES monitors the magnitude of gradient changes for each matrix during training and individually freezes components that fall below a convergence threshold. This method is shown to speed up training time by 1.57x to 7.22x while also enhancing model generalization by preventing overfitting, leading to higher average accuracy on both language and multimodal tasks.

## Architecture Overview

![GradES Architecture](/images/grades-architecture.png)
*GradES architecture showing component-level gradient monitoring. Colors indicate gradient magnitude changes for each weight matrix. Components with low gradient changes (below threshold τ) are frozen while others continue training.*

## Convergence Behavior

![Gradient Convergence](/images/grades-convergence.png)
*Element-wise L₁ norms for gradient matrices of components in layer 7 for Qwen3-0.6B. MLP projections exhibit 2-3× higher gradient magnitudes than attention projections throughout training, with different convergence rates for each component.*

**Key Observations:**
- MLP components (mlp_up_proj, mlp_down_proj, mlp_gate_proj) maintain larger gradient magnitudes
- Attention projections (attn_q_proj, attn_k_proj, attn_v_proj, attn_o_proj) converge faster
- The freeze threshold (τ = 1.183 × 10⁻³) is set to identify truly converged components
- Different components require different amounts of training, validating the component-level approach

## Key Contributions

- **Component-Level Convergence Detection**: Tracks element-wise L1 norm of gradient changes for each individual weight matrix instead of global validation loss
- **Adaptive Grace Period**: Initial training phase where no freezing occurs, allowing all components to adapt from pre-trained initialization
- **Selective Freezing**: Stops parameter updates for converged components while maintaining gradient flow for stable training
- **Compatibility**: Seamlessly integrates with both full-parameter fine-tuning and PEFT methods like LoRA

## Results

### Training Efficiency
- **Full-Parameter Fine-tuning**: 1.32x-1.64x speedup, 29-45% reduction in FLOPs
- **LoRA Fine-tuning**: 2.66x-7.22x speedup compared to full-parameter baselines
- **vs Classic Early Stopping**: GradES provides speedup while classic ES often slows training (0.59x-0.76x)

### Model Accuracy
- Consistently maintains or improves model accuracy by preventing overfitting
- **Language Models**: Competitive or highest accuracy across benchmarks (e.g., 91.94% on Phi4 14B)
- **Vision-Language Models**: Average accuracy increase of 3.88 percentage points on nanoVLM

### Models Evaluated
- **Language Models**: Qwen3-14B, Microsoft Phi4-14B, Llama-3.1-8B-Instruct, Mistral-7B-Instruct-v0.3, Qwen3-0.6B
- **Vision-Language Models**: Qwen2.5-VL-7B, nanoVLM

### Benchmarks
- **Language**: BoolQ, PIQA, SIQA, HellaSwag, OpenBookQA, ARC-Easy, ARC-Challenge, WinoGrande
- **Vision-Language**: GQA, VQAv2, COCO Captions

## Key Insights

Different components in transformer models have distinct convergence behaviors:
- **MLP vs Attention**: MLP components consistently have larger gradient norms and converge more slowly
- **Language vs Vision**: In VLMs, language components converge much faster than vision components
- This heterogeneity motivates component-specific stopping criteria rather than global model-wide decisions
