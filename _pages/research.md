---
title: "Research"
permalink: /research/
no_prose: true
toc:
  - id: newton
    title: "Newton-type methods for nonsmooth optimization"
  - id: stability
    title: "Stability of regularized inverse problems"
  - id: applications
    title: "PDE control and machine learning"
  - id: pde
    title: "Earlier work: p-Laplace equations"
lede: "I work in continuous optimization and variational analysis. Many problems in data science, imaging, and engineering lead to optimization models with kinks, corners, or constraints, where classical derivatives break down. My research uses generalized differentiation to answer two practical questions about such problems: how to solve them fast, and when their solutions can be trusted."
---

<section class="direction-section" id="newton" markdown="1">

## Fast Newton-type methods for nonsmooth optimization

<div class="prose" markdown="1">

Many models in statistics, signal processing, and machine learning have the form $$\min_x f(x) + g(x)$$: a smooth data-fitting term $$f$$ plus a nonsmooth regularizer $$g$$ that encodes structure, such as sparsity (Lasso), grouped variables (Group Lasso), or piecewise-constant signals (total variation). First-order methods such as proximal gradient (ISTA/FISTA) are simple and cheap per step, but they become very slow when high accuracy is needed. Newton's method converges much faster, but it needs second derivatives, which the regularizer $$g$$ does not have.

Our approach is built on *effective subspaces*. Near a solution, a polyhedral regularizer is linear along certain directions. A cheap proximal step identifies this subspace, and a Newton step restricted to it needs only the Hessian of $$f$$ and first-order information about $$g$$. We prove local quadratic convergence under tilt stability, without the strict complementarity (nondegeneracy) assumptions common in earlier work, and we give explicit formulas for the $$\ell_1$$, $$\ell_\infty$$, OSCAR/SLOPE, and total-variation regularizers. Current work extends the idea to generalized equations and to the non-polyhedral Group Lasso, and develops Newton methods that converge globally while working with the nonsmooth problem directly rather than with a smooth surrogate of it.

</div>

<div class="bleed">
{% include paper-figure.html src="paper/newton-superres.webp" alt="Three microscopy images: a sharp ground-truth image of eight wavy filaments, a blurry low-resolution average, and a sharp reconstruction." caption="Super-resolution fluorescence microscopy, one of the applications in our *Mathematics of Operations Research* paper (SMLM ISBI 2013 data). Left: high-resolution ground truth. Middle: the data actually observed, the average of 361 low-resolution 64×64 frames. Right: the 256×256 reconstruction computed with our FISTA–Newton method from a Poisson (Kullback–Leibler) data term with an ℓ1 penalty and nonnegativity." %}
</div>

<div class="prose">
  <a class="inline-cta" href="{{ '/research/newton-methods/' | relative_url }}">Read the illustrated introduction to this direction</a>
  <div class="papers">
    <h3>Papers</h3>
    <ol class="pub-list">
      {% assign tp = site.publications | where: "theme", "newton" | sort: "cv_order" %}
      {% for post in tp %}{% include nv-pub.html pub=post %}{% endfor %}
    </ol>
  </div>
  <p class="collaborators">With Tran T. A. Nghia, Khoa V. H. Vu, and Samik Barman.</p>
</div>

</section>

<section class="direction-section" id="stability" markdown="1">

## Stability of regularized inverse problems

<div class="prose" markdown="1">

In an inverse problem we want an unknown signal or image $$x_0$$, but we only see indirect, noisy measurements $$y \approx \Phi x_0$$. Examples include MRI, deblurring, and compressed sensing, where there are far fewer measurements than unknowns. Regularizing with a convex penalty such as the $$\ell_1$$ norm, the group $$\ell_1/\ell_2$$ norm, or total variation selects a structured solution. The question I study is reliability. If the noise has size $$\delta$$, is the computed solution within $$O(\delta)$$ of the truth? This property is called *stable recovery*. A closely related property, *isolated calmness*, asks that the solution move at most linearly when the data move.

Classical sufficient conditions rely on sharp minima and on first-order information about the regularizer. We showed that the exact condition is second-order: stable recovery holds if and only if the kernel of $$\Phi$$ meets a certain tangent cone, built from the subdifferential of the regularizer, only at zero. For piecewise linear-quadratic regularizers, such as $$\ell_1$$, total variation, and the elastic net, this reduces to something familiar: stable recovery is equivalent to the true signal being the unique solution. The same tangent-cone condition characterizes isolated calmness. For analysis-sparsity models it can be checked by solving linear programs. We also give a group-sparsity example where the solution is unique but not calm, so non-polyhedral regularizers genuinely need the second-order theory. Ongoing work studies full Lipschitz stability of the solution map.

</div>

<div class="bleed">
{% include paper-figure.html src="paper/stable-recovery-rates.webp" alt="Two line charts of recovery rate versus number of measurements, each with three curves: recovered, sharp, and strong but non-sharp solutions." caption="How often recovery succeeds as the number of random Gaussian measurements $$m$$ grows (100 trials per $$m$$). Left: group sparsity, with signals in ℝ<sup>2000</sup> and 10 of 100 groups active. Right: isotropic total variation on 28×28 images. Green: the true signal is recovered. Blue: it is a sharp solution, the case covered by classical stability theory. Red: it is recovered as a strong but non-sharp solution, so first-order theory cannot certify stability; our second-order conditions are designed for exactly these cases. From *Inverse Problems* 41 (2025)." %}
</div>

<div class="prose">
  <div class="papers">
    <h3>Papers</h3>
    <ol class="pub-list">
      {% assign tp = site.publications | where: "theme", "stability" | sort: "cv_order" %}
      {% for post in tp %}{% include nv-pub.html pub=post %}{% endfor %}
    </ol>
  </div>
  <p class="collaborators">With Tran T. A. Nghia, Huy N. Pham, and Khoa V. H. Vu.</p>
</div>

</section>

<section class="direction-section" id="applications" markdown="1">

## Nonconvex optimization in PDE control and machine learning

<div class="prose" markdown="1">

Two applied projects take these tools to settings where convexity is lost.

### PDE-constrained optimization

In optimal control we choose a control, for example a heat source spread over a plate, so that the resulting state, governed by a partial differential equation, is close to a target. Sparse controls that act only on small regions are often preferable. The nonconvex $$L^1-L^2$$ penalty promotes sparsity more strongly than $$L^1$$ alone, and it gives the problem a *difference-of-convex* (DC) structure. We designed I-ADCA, an inexact and accelerated DC algorithm in Hilbert spaces. Each step may use an inexact subgradient and solve its convex PDE subproblem only approximately, as happens in practice, yet the method still converges to stationary points, with explicit rates under a Polyak–Łojasiewicz-type condition. Combined with finite elements, it comes with error bounds for the discretized problem. On the finest mesh in the paper (16,129 unknowns), it needed about half the CPU time of the classical DC algorithm.

</div>

<div class="bleed">
{% include paper-figure.html src="paper/dc-control.webp" width="36rem" alt="Two 3D surface plots on the unit square: a smooth desired state, and an optimal control that is exactly zero on a band of the domain." caption="An elliptic optimal control problem with the $$L^1-L^2$$ penalty and box constraints. Left: desired state. Right: optimal control computed by I-ADCA with finite elements; it is exactly zero on large parts of the domain. From Khanh, Khoa, Mordukhovich, Tran, and Vo (submitted)." %}
</div>

<div class="prose" markdown="1">

### Knowledge distillation

Large neural networks are accurate but expensive to deploy. Knowledge distillation trains a small *student* network to imitate the softened predictions, or soft labels, of a large *teacher*. The softening is controlled by a temperature, traditionally one fixed number for all data. We showed that the information content (entropy) of a soft label is governed mainly by the ratio between the teacher's largest logit and the temperature. With one fixed temperature, some soft labels are therefore nearly one-hot and others nearly uniform. Our method, CIST, picks the temperature for each sample, separately for teacher and student, so that every soft label is similarly informative. It improves standard distillation and strong baselines on CIFAR-100, ImageNet, and language-model distillation, at negligible extra cost. For example, a ResNet8×4 student distilled from a ResNet32×4 teacher on CIFAR-100 goes from 73.33% to 76.96% top-1 accuracy.

</div>

<div class="bleed">
{% include paper-figure.html src="paper/cist-entropy.webp" width="30rem" alt="Box plots of soft-label entropy for four teacher networks: wide boxes with many low outliers for a fixed temperature, narrow boxes for CIST." caption="Entropy of the teacher's soft labels on CIFAR-100 for four teacher networks. With a fixed temperature the entropies are widely spread, with many low-entropy outliers; CIST concentrates them. From Luong, Vo, Zhao, and Chen (submitted to AISTATS 2027)." %}
</div>

<div class="prose">
  <div class="papers">
    <h3>Papers</h3>
    <ol class="pub-list">
      {% assign tp = site.publications | where: "theme", "applications" | sort: "cv_order" %}
      {% for post in tp %}{% include nv-pub.html pub=post %}{% endfor %}
    </ol>
  </div>
  <p class="collaborators">With P. D. Khanh, V. V. H. Khoa, B. S. Mordukhovich, and D. B. Tran (DC algorithms), and with Hoang-Chau Luong, Kaiqi Zhao, and Lingwei Chen (knowledge distillation).</p>
</div>

</section>

<section class="direction-section" id="pde" markdown="1">

## Earlier work: regularity theory for p-Laplace equations

<div class="prose" markdown="1">

Before moving to optimization, during my undergraduate studies in Ho Chi Minh City, I worked on the regularity of solutions to quasilinear elliptic equations of p-Laplace type. These equations model nonlinear diffusion and non-Newtonian flow. The basic question: if the data of the equation are controlled in some function space, how well behaved is the gradient of the solution? We proved gradient estimates expressed through fractional maximal operators, in Morrey spaces and in weighted Lorentz spaces.

</div>

<div class="prose">
  <div class="papers">
    <h3>Papers</h3>
    <ol class="pub-list">
      {% assign tp = site.publications | where: "theme", "pde" | sort: "cv_order" %}
      {% for post in tp %}{% include nv-pub.html pub=post %}{% endfor %}
    </ol>
  </div>
  <p class="collaborators">With Cao-Kha Doan, Gia-Bao Nguyen, Thanh-Nhan Nguyen, and Minh-Phuong Tran.</p>
</div>

</section>
