---
title: "Model Compression using Adaptive Knowledge Distillation"
excerpt: "Per-sample soft-label temperatures (CIST) for training smaller neural networks that stay accurate under resource constraints."
collection: portfolio
---

Developed CIST (Consistently Informative Soft-label Temperature), a knowledge-distillation approach that helps smaller neural networks mimic larger models for faster and cheaper deployment on resource-constrained platforms. See the paper: [Consistently informative soft-label temperature for knowledge distillation](/publication/2026-consistently-informative-soft-label-temperature) (arXiv:2605.20357).

CIST achieved up to a 3.63-point accuracy gain over standard knowledge distillation at negligible additional training cost, with results across CNN architectures including ResNet, VGG, WideResNet, MobileNet, and ShuffleNet on CIFAR-100 and ImageNet, and on language-model distillation.
