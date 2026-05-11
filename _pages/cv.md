---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

[Download CV as PDF](/files/Nghia_Van_Vo_CV.pdf)

Summary
======

Computational researcher in applied mathematics, optimization, and machine learning with experience designing and analyzing optimization algorithms for large-scale machine learning models. My work translates mathematical optimization into high-performance implementations, including modern fine-tuning and model-compression techniques that make models smaller and more accurate.

Education
======
* Ph.D. in Applied Mathematics, Oakland University, Rochester, Michigan, 2022-present
* M.S. in Applied Statistics, Oakland University, Rochester, Michigan
* Mathematics Teacher Education, University of Education, Ho Chi Minh City, Vietnam, 2017-2021

Relevant Coursework
======
Machine Learning; Deep Learning; Advanced Convex Optimization; Nonlinear Programming; Applied Linear Models; Experimental Design; Mathematical Statistics; Time Series; Numerical Methods for PDEs; Numerical Matrix Algorithms.

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% unless post.category == "hidden" %}
      {% include archive-single-cv.html %}
    {% endunless %}
  {% endfor %}</ul>

Projects
======
  <ul>{% for post in site.portfolio %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Honors and Awards
======
* McKay Outstanding Graduate Research Fellowship, Oakland University, 2026
* Travel Grant to attend Midwest Optimization Meeting, University of North Dakota, 2025
* Travel Grant to attend East Coast Optimization Meeting, George Mason University, 2025
* Travel Grant to attend Midwest Optimization Meeting, University of Michigan, 2023
* Award for Teaching Excellence Internship, Department of Mathematics, Binh Phu High School, 2021
* First Prize, Department of Mathematics Undergraduate Scientific Research Competition, 2020
* First Prize, Undergraduate Scientific Research Competition, H.C.M City University of Education, 2020

Skills
======
* Programming: Python, Matlab, SAS, C, SQL
* Optimization: gradient descent, stochastic gradient descent, proximal methods, FISTA, Newton methods, ADMM, Douglas-Rachford, Chambolle-Pock primal-dual, coordinate descent
* Frameworks and tools: Scikit-learn, PyTorch, Pandas, NumPy, Matplotlib, Seaborn, CVXPY, Gurobi, CPLEX, MATLAB Optimization Toolbox, Git, GitHub
* Languages: English, Vietnamese

Certificates
======
* Introduction to Data Analytics in Google Cloud
* Machine Learning Specialization, Stanford University and Coursera
* Scientific Computing and Data Analysis with Python, FreeCodeCamp
* Mathematics for Machine Learning, Imperial College London and Coursera
