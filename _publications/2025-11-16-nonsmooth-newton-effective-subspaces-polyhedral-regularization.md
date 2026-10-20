---
title: "Nonsmooth Newton methods with effective subspaces for polyhedral regularization"
collection: publications
category: articles
cv_order: 1
permalink: /publication/2025-nonsmooth-newton-effective-subspaces-polyhedral-regularization
date: 2026-09-01
authors: "Tran T. A. Nghia, <strong>Nghia V. Vo</strong>, and Khoa V. H. Vu"
venue: "Mathematics of Operations Research"
venue_line: "Mathematics of Operations Research, to appear (accepted September 2026)"
status: "To appear"
arxiv: "https://arxiv.org/abs/2511.16514"
paperurl: "https://arxiv.org/abs/2511.16514"
theme_url: /research/newton-methods/
theme_label: "Plain-language overview"
summary: "Newton-type methods for problems with polyhedral regularizers (Lasso, ℓ∞, OSCAR/SLOPE, total variation) that use only first-order information about the regularizer and converge quadratically under tilt stability."
citation: "Tran T. A. Nghia, Nghia V. Vo, and Khoa V. H. Vu. Nonsmooth Newton methods with effective subspaces for polyhedral regularization. <i>Mathematics of Operations Research</i>, to appear. arXiv:2511.16514."
bibtex: |
  @article{NghiaVoVu2026Newton,
    title   = {Nonsmooth {N}ewton methods with effective subspaces for polyhedral regularization},
    author  = {Nghia, Tran T. A. and Vo, Nghia V. and Vu, Khoa V. H.},
    journal = {Mathematics of Operations Research},
    note    = {To appear. arXiv:2511.16514},
    year    = {2026}
  }
theme: newton
overview: true
selected: 1
---

We develop nonsmooth Newton methods for convex composite problems $$\min_x f(x) + g(x)$$, where $$f$$ is smooth and $$g$$ is a polyhedral regularizer such as the $$\ell_1$$ norm, the $$\ell_\infty$$ norm, the sorted $$\ell_1$$ (OSCAR/SLOPE) norm, or the one-dimensional total variation. The Newton step is computed on an *effective subspace* built from first-order information about the regularizer, so no generalized Hessian of $$g$$ is needed. When the minimizer is tilt-stable, the methods converge quadratically, without requiring strict complementarity. Experiments on Lasso, generalized Lasso, OSCAR-regularized least squares, and an image super-resolution task show faster convergence than first-order methods and several recent nonsmooth Newton methods.

