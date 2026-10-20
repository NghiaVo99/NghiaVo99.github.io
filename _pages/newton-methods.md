---
title: "Newton-type methods for nonsmooth optimization"
permalink: /research/newton-methods/
kicker: "Research"
kicker_url: /research/
lede: "A short, illustrated introduction to my main research direction: how to get Newton's fast convergence on problems whose regularizer has corners."
no_prose: true
toc:
  - id: problem
    title: "The problem"
  - id: idea
    title: "The idea"
  - id: results
    title: "What we prove"
  - id: practice
    title: "On real problems"
  - id: papers
    title: "Papers"
---

<div class="prose" markdown="1">

## Smooth data fit plus a nonsmooth regularizer {#problem}

A large class of models in statistics, imaging, and machine learning asks us to solve

$$\min_{x}\; f(x) + g(x),$$

where $$f$$ is a smooth loss that fits the data (least squares, logistic loss, a Poisson likelihood) and $$g$$ is a regularizer that enforces structure in the solution. Many of the most useful regularizers are *polyhedral*: their level sets are polytopes with flat faces, corners, and edges. Sparse solutions sit exactly at those corners, which is why such regularizers produce sparse or piecewise-constant answers.

</div>

<div class="bleed">
{% include theme-figure.html name="polyhedral-balls" width="40rem" alt="Unit balls of the l1 norm (a diamond), the l-infinity norm (a square), and the OSCAR regularizer (an octagon)." caption="Unit balls of three polyhedral regularizers covered by our theory: the ℓ1 norm (Lasso), the ℓ∞ norm, and OSCAR, a special case of the sorted ℓ1 norm (SLOPE). One-dimensional total variation is another example. The corners make solutions sparse; the flat faces are what our method exploits." %}
</div>

<div class="prose" markdown="1">

The difficulty is that $$g$$ has no second derivative at exactly the points we care about. First-order methods such as ISTA and FISTA only need the proximal map of $$g$$, but they converge slowly once high accuracy is required. Newton's method is fast, but it needs curvature that $$g$$ does not have.

## Find the flat directions, then take a Newton step there {#idea}

On a face of a polyhedral regularizer, $$g$$ is *linear*, so it adds no curvature at all. If we knew which face the solution lies on, we could restrict the problem to that face, where only the smooth part $$f$$ is curved, and take an ordinary Newton step. The directions along that face form what we call the **effective subspace**. Our methods find it from information that first-order methods already compute: one proximal-gradient step produces a point $$y$$ and a subgradient $$z$$ of $$g$$ at $$y$$, and the effective subspace is read off from $$z$$, as the parallel space of $$\partial g^*(z)$$. Then a Newton step is taken inside that subspace.

</div>

<div class="bleed">
{% include theme-figure.html name="polyhedral-idea" width="42rem" alt="Two contour plots of the same objective. Top: forty orange proximal-gradient steps creep along the horizontal axis toward the minimizer. Bottom: blue arrows show the Newton variant reaching the minimizer in three steps." caption="A two-dimensional toy example made for this page: an ℓ1-regularized quadratic whose minimizer lies on the $$x_1$$-axis, the effective subspace. Top: proximal gradient (ISTA) quickly reaches the axis, then creeps toward the minimizer; after 40 steps it is still short. Bottom: the ISTA–Newton method alternates a proximal step with a Newton step inside the identified subspace and lands on the minimizer in three steps." %}
</div>

<div class="prose" markdown="1">

For the ℓ1 norm the recipe is very concrete: the effective subspace consists of the coordinates where the subgradient $$z_i$$ equals $$\pm\lambda$$, and the Newton step solves a small linear system on those coordinates only. We derive similarly explicit formulas for the ℓ∞ norm, the sorted ℓ1 norm (OSCAR/SLOPE), and one-dimensional total variation.

## What we prove {#results}

<div class="callout" markdown="1">
- **Fast.** If the minimizer is *tilt-stable*, a standard second-order stability property, the ISTA–Newton method converges quadratically from nearby starting points: the number of correct digits roughly doubles at each step.
- **Weak assumptions.** No strict complementarity or nondegeneracy condition is needed. The paper gives an example where that condition fails and quadratic convergence still holds.
- **Cheap.** Only the proximal map of $$g$$ and the Hessian of $$f$$ on a subspace are used. No generalized Hessian of the regularizer is needed.
- **Practical.** An accelerated variant (FISTA–Newton) and line-search versions work well in practice. Away from the solution, each iteration costs about as much as a first-order step.
</div>

## What it looks like on real problems {#practice}

</div>

<div class="bleed">
{% include paper-figure.html src="paper/newton-lasso.png" alt="Three panels comparing nine methods on a Lasso problem: objective gap and distance to the solution versus iteration on log scales, and a bar chart of runtimes." caption="Lasso test from the paper (48 measurements, 128 unknowns, 8 nonzeros): objective gap, distance to the solution, and runtime. The effective-subspace methods (Newton_ISTA, Newton_FISTA, and their line-search variants) are compared with ISTA, FISTA, and three recent second-order methods (SSNAL, GRNM, GSSN). Once the subspace is identified, the effective-subspace methods reach the tolerance within a few iterations, and they have the four shortest runtimes." %}
</div>

<div class="prose" markdown="1">

The paper reports the same behavior for the ℓ∞ norm, OSCAR, and total-variation problems, and for super-resolution microscopy with Poisson noise, shown on the [Research page]({{ '/research/' | relative_url }}#newton).

## Where this direction is going {#papers}

</div>

<div class="prose">
  <ol class="pub-list">
    {% assign tp = site.publications | where: "theme", "newton" | sort: "cv_order" %}
    {% for post in tp %}{% include nv-pub.html pub=post %}{% endfor %}
  </ol>
</div>
