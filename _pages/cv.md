---
title: "Curriculum vitae"
permalink: /cv/
no_prose: true
aside: aside-cv.html
toc:
  - id: education
    title: "Education"
  - id: interests
    title: "Research interests"
  - id: publications
    title: "Publications"
  - id: talks
    title: "Talks"
  - id: teaching
    title: "Teaching"
  - id: honors
    title: "Honors and awards"
  - id: skills
    title: "Skills"
redirect_from:
  - /resume
---
{% assign pubs = site.publications | where_exp: "p", "p.cv_order" | sort: "cv_order" %}
<div class="prose">
  <section class="cv-section">
    <h2 id="education">Education</h2>
    <ul class="rows">
      <li><span class="rows__when">2022–present</span><div><p class="rows__what">Ph.D. in Applied Mathematics</p><p class="rows__where">Oakland University, Rochester, Michigan. Advisor: Tran T. A. Nghia. Expected May 2027.</p></div></li>
      <li><span class="rows__when">2022–2024</span><div><p class="rows__what">M.S. in Applied Statistics</p><p class="rows__where">Oakland University, Rochester, Michigan</p></div></li>
      <li><span class="rows__when">2017–2021</span><div><p class="rows__what">B.S. in Applied Mathematics</p><p class="rows__where">University of Education, Ho Chi Minh City, Vietnam</p></div></li>
    </ul>
  </section>

  <section class="cv-section">
    <h2 id="interests">Research interests</h2>
    <p style="margin-top:0.9rem">Convex and nonconvex optimization; nonlinear optimization; variational analysis; mathematical programming; stability theory; stochastic optimization algorithms.</p>
  </section>

  <section class="cv-section">
    <h2 id="publications">Publications</h2>
    {% assign groups = "articles|Published and accepted,submitted|Submitted,preprints|Preprints" | split: "," %}
    {% for g in groups %}
      {% assign parts = g | split: "|" %}
      {% assign items = pubs | where: "category", parts[0] %}
      <h3 class="cv-sub">{{ parts[1] }}</h3>
      <ol class="pub-list">
        {% for post in items %}{% include nv-pub.html pub=post num=post.cv_order %}{% endfor %}
      </ol>
    {% endfor %}
  </section>

  <section class="cv-section">
    <h2 id="talks">Talks</h2>
    <ul class="rows">
      {% for t in site.data.talks %}
      <li><span class="rows__when">{{ t.when }}</span><div><p class="rows__what">{{ t.title }}</p><p class="rows__where">{{ t.venue }}</p></div></li>
      {% endfor %}
    </ul>
  </section>

  <section class="cv-section">
    <h2 id="teaching">Teaching experience</h2>
    <ul class="rows">
      <li><span class="rows__when">2022–present</span><div>
        <p class="rows__what">Workshop Instructor and Tutor</p><p class="rows__where">Oakland University</p>
        <div class="rows__detail"><ul>
          <li>Workshop instructor for Elementary Algebra, Intermediate Algebra, and Precalculus, teaching about 80 students through guided questioning and student-developed solutions.</li>
          <li>Weekly tutor at the Math Help Center for Algebra, Calculus I and II, and Multivariable Calculus.</li>
          <li>Grader for Mathematical Analysis for Engineers I and II and Introduction to Differential Equations with Matrix Algebra.</li>
        </ul></div>
      </div></li>
      <li><span class="rows__when">Summer 2024</span><div>
        <p class="rows__what">Mathematics Teacher, Boys in Engineering Academy</p><p class="rows__where">The Engineering Society of Detroit</p>
        <div class="rows__detail"><ul>
          <li>Facilitated hands-on, project-based mathematics and STEM activities for Detroit middle school students.</li>
          <li>Mentored small groups and helped students connect quantitative reasoning with engineering design.</li>
        </ul></div>
      </div></li>
      <li><span class="rows__when">Summer 2023</span><div>
        <p class="rows__what">Teaching Fellow, Introduction to Computational Thinking and Scratch Programming</p><p class="rows__where">STEAM for Vietnam Foundation</p>
        <div class="rows__detail"><ul>
          <li>Helped deliver a train-the-trainer program for about 4,000 Vietnamese teachers on the Scratch programming language.</li>
          <li>Trained and mentored nearly 60 teaching assistants; developed curriculum and training materials.</li>
        </ul></div>
      </div></li>
    </ul>
  </section>

  <section class="cv-section">
    <h2 id="honors">Honors and awards</h2>
    {% include nv-award-rows.html items=site.data.awards %}
  </section>

  <section class="cv-section">
    <h2 id="skills">Skills</h2>
    <dl class="skills">
      <dt>Programming and development</dt><dd>Python, MATLAB, SAS, C, SQL; Git and GitHub</dd>
      <dt>Optimization algorithms</dt><dd>Gradient and stochastic gradient methods, proximal methods and FISTA, Newton methods, coordinate descent, ADMM, Douglas–Rachford splitting, the Chambolle–Pock primal–dual method</dd>
      <dt>Scientific computing and machine learning</dt><dd>NumPy, Pandas, Scikit-learn, PyTorch, Matplotlib, Seaborn</dd>
      <dt>Optimization software</dt><dd>CVXPY, Gurobi, CPLEX, MATLAB Optimization Toolbox</dd>
      <dt>Certificates</dt><dd>Machine Learning Specialization (Stanford University and Coursera); Mathematics for Machine Learning (Imperial College London and Coursera); Scientific Computing and Data Analysis with Python (freeCodeCamp); Introduction to Data Analytics in Google Cloud</dd>
      <dt>Languages</dt><dd>English, Vietnamese</dd>
    </dl>
  </section>
</div>
