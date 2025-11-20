---
permalink: /
title: "About Me"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

I'm Zihan Zhou, a Master's graduate from Boston University actively seeking PhD opportunities in **Machine Learning** and **Computer Vision** starting Fall 2026. My research focuses on developing efficient and scalable machine learning systems that bridge the gap between theoretical foundations and practical applications.

Currently, I work as a Research Assistant at Boston University under the supervision of Prof. Reza Rawassizadeh and Prof. Avi Mohan, conducting research on efficient training methods, federated learning, and computer vision.

## Research Interests

My work spans several cutting-edge areas in machine learning and computer vision:

- **Efficient Training Methods**: Developing gradient-based early stopping techniques for transformers that achieve 1.5x-7x training speedup
- **3D Vision & World Models**: Exploring novel approaches to scene understanding and temporal prediction
- **Federated Learning**: Investigating convergence theory and practical implementations for heterogeneous distributed systems
- **Continual Learning**: Researching methods to prevent catastrophic forgetting in sequential learning tasks
- **Pose Estimation & Motion Reconstruction**: Building pipelines for motion capture and 3D character animation

## Current Research Projects

### GradES: Gradient-Based Early Stopping for Transformers
**Advisor:** Prof. Reza Rawassizadeh | [arXiv:2509.01842](https://arxiv.org/abs/2509.01842)

Co-authored a paper on component-level early stopping that speeds up transformer training by 1.5x-7x while improving generalization. The method monitors gradient magnitudes at the individual weight matrix level, eliminating expensive validation passes.

<div style="text-align: center; margin: 20px 0;">
  <img src="/images/grades-convergence.png" alt="GradES Gradient Convergence Analysis" style="max-width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
  <p style="font-size: 0.9em; color: #666; margin-top: 10px;"><em>Gradient convergence behavior across transformer components in layer 7 for Qwen3-0.6B, showing distinct convergence rates between MLP and attention projections.</em></p>
</div>

**Key Results:**
- 29-45% reduction in FLOPs compared to standard fine-tuning
- Consistent accuracy improvements across language and vision-language models
- Tested on models from 0.6B to 14B parameters (Qwen, Phi4, Llama, Mistral)

### 3D Scene Understanding and Prediction
Developing novel approaches for world modeling that combine scene reconstruction with temporal dynamics using neural representations.

**Target:** CVPR 2026

### Federated Learning: Theory and Practice
**Advisor:** Prof. Avi Mohan

Investigating convergence theory in federated learning systems through empirical validation on object detection tasks and controlled experiments with heterogeneous data distributions.

### Continual Learning in Sequential Tasks
Exploring methods to mitigate catastrophic forgetting in sequential learning scenarios, with focus on maintaining performance across multiple tasks.

**Target:** ICLR 2026

## Education

**Master of Science in Computer Science** | Boston University (2023 - 2025)
- Research focus: Machine Learning, Computer Vision, Federated Learning

**Bachelor of Science in Computer Science** | Hobart and William Smith Colleges (2019 - 2023)
- Location: Geneva, NY

## Technical Skills

- **Deep Learning Frameworks:** PyTorch, TensorFlow
- **Computer Vision:** 3D Gaussian Splatting, Pose Estimation, Object Detection
- **Distributed Systems:** Federated Learning (Flower), Multi-GPU Training
- **Research Tools:** Wandb, Git, Docker, Jupyter
