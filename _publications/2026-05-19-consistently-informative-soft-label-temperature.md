---
title: "Consistently informative soft-label temperature for knowledge distillation"
collection: publications
category: submitted
cv_order: 8
permalink: /publication/2026-consistently-informative-soft-label-temperature
redirect_from:
  - /publication/2026-adaptive-temperature-scaling-knowledge-distillation
date: 2026-05-19
authors: "Hoang-Chau Luong, <strong>Nghia V. Vo</strong>, Kaiqi Zhao, and Lingwei Chen"
venue: "AISTATS 2027 (submitted)"
venue_line: "Submitted to the International Conference on Artificial Intelligence and Statistics (AISTATS 2027)"
status: "Submitted"
arxiv: "https://arxiv.org/abs/2605.20357"
paperurl: "https://arxiv.org/abs/2605.20357"
theme_url: /research/#applications
summary: "Per-sample temperatures for teacher and student in knowledge distillation, so every soft label carries a similar amount of information."
citation: "Hoang-Chau Luong, Nghia V. Vo, Kaiqi Zhao, and Lingwei Chen. Consistently informative soft-label temperature for knowledge distillation. Submitted to AISTATS 2027. arXiv:2605.20357."
theme: applications
selected: 4
---

Knowledge distillation trains a small student network to match the softened predictions of a large teacher. A single fixed temperature treats all samples alike, so some soft labels are nearly one-hot while others are almost uniform, and teacher and student are forced onto the same logit scale. We propose CIST, which assigns adaptive per-sample temperatures to teacher and student separately and reweights the distillation loss by teacher confidence and student difficulty. We show that the entropy of a teacher's soft label is governed mainly by the ratio of its largest logit to the temperature, which motivates the design. CIST improves standard distillation and strong baselines on image classification (CIFAR-100, ImageNet) and language-model distillation, at negligible extra cost.
