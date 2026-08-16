---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 1: Linear Systems

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask who has ever tried to double a recipe and had it come out
wrong anyway. That familiar frustration is today's hook.
-->

---

<!-- SLOT 2: Where we are -->

# Where We Are

<div class="roadmap">
<div class="wk now"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
<div class="wk"><div class="n">Wk 5</div><div class="t">Factorization</div></div>
<div class="wk"><div class="n">Wk 6</div><div class="t">Determinants</div></div>
<div class="wk"><div class="n">Wk 7</div><div class="t">Vector Spaces · Quiz 1</div></div>
<div class="wk review"><div class="n">Wk 8</div><div class="t">Midterm Exam</div></div>
<div class="wk"><div class="n">Wk 9</div><div class="t">Bases, Dimension</div></div>
<div class="wk"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: Point out the arc: solve, represent, transform, compute, measure, approximate. Fifteen weeks, one growing toolkit. -->

---

<!-- SLOT 3: What you already bring -->

# What You Already Bring

No formal prerequisite is required for this course, but you are not
starting from zero:

- **High school algebra**: you have solved two equations in two unknowns before, usually by substitution
- **Computer Programming**: you already think in terms of variables holding values and operations applied to them, the same habit of mind this course formalizes
- **Basic arithmetic with fractions and negatives**: the only computational tool this course truly assumes

We are not teaching new arithmetic. We are teaching a systematic way to
handle many equations at once, exactly, without guessing.

---

<!-- Course logistics appendix -->

<!-- _class: section -->

# Course Logistics
<div class="driving-q">Read once now, referenced all semester.</div>

---

# Grading & Materials

| Item | Weight |
|---|---|
| Attendance | 10% |
| Midterm | 30% |
| Final | 30% |
| Assignments | 10% |
| In-class items | 20% |

<!-- notes: Assignment 1 due Week 4 (Matrix Algebra). Assignment 2 due Week 11 (Diagonalization). Quiz 1 Week 7 (Vector Spaces), Quiz 2 Week 14 (Least Squares). -->

---

# Textbook, Policy & Contact

- **Textbook:** Lay, Lay & McDonald, *Linear Algebra and Its Applications*, 6th ed., Pearson, 2020
- **References:** Hefferon, *Linear Algebra*, 4th ed. (open textbook); Cherney, Denton, Thomas & Waldron, *Linear Algebra*, UC Davis, 2013
- **Policy:** attend and participate every class; late assignments are penalized; plagiarism and cheating lead to disciplinary action
- **Contact:** yushintia@deu.ac.kr, office hours by email appointment

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# A Recipe That Doubles Badly

<div class="pain">

The Campus Café's signature drink uses three ingredients in a fixed
balance: espresso, milk, and syrup. It tastes right for one cup. A
professor books the café to cater a 200-person department event, same
drink, same taste, just more of it.

The barista does what feels natural: multiply everything by 200. Batch
after batch comes out wrong: too sweet, not sweet enough, and once
noticeably too strong. Different staff members "eyeball" the scale-up
differently, and none of their guesses agree. By the end of the shift,
three large batches are poured down the drain, and the department event
still doesn't have enough of the drink it ordered.

</div>

<!-- notes: Do not use the word "equation" or "matrix" yet. Let the wasted batches sit uncomfortably first. -->

---

# Guessing Gets Worse, Not Better, at Scale

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">1 cup, by feel</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">usually fine</div>
</div>
<div class="bar-row">
  <div class="bar-label">10 cups, "just multiply"</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 45%"></div></div>
  <div class="bar-value">taste starts drifting</div>
</div>
<div class="bar-row">
  <div class="bar-label">200 cups, department order</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">three batches, wasted</div>
</div>
</div>

Guessing does not scale linearly with the problem. This course teaches
the exact method that does.

<!-- notes: Let the widening bars sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What Else This Actually Costs

- Wasted ingredients are wasted money, every single time a batch is poured out
- A structural engineer who cannot solve linked load equations exactly risks a design that looks fine on paper and fails in practice
- A navigation app that cannot solve its positioning equations exactly gives you the wrong street, not an approximately right one

<div class="why">
<strong>In industry:</strong> "set up and solve this system" underlies
GPS positioning, computer graphics transformations, economic models, and
the training of every machine learning model you will meet later in this
major. It is one of the most common building blocks in technical
interviews across engineering and data science.
</div>

---

# The Same Problem, Bigger Every Time

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">3 ingredients, 1 recipe</div>
  <div class="bar-track"><div class="bar-fill risk-low" style="width: 20%"></div></div>
  <div class="bar-value">solvable by hand, carefully</div>
</div>
<div class="bar-row">
  <div class="bar-label">GPS: 4 satellites, 4 unknowns</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 55%"></div></div>
  <div class="bar-value">solved by your phone, every second</div>
</div>
<div class="bar-row">
  <div class="bar-label">ML model: millions of parameters</div>
  <div class="bar-track"><div class="bar-fill risk-high" style="width: 92%"></div></div>
  <div class="bar-value">impossible without a systematic method</div>
</div>
</div>
<div class="bar-note">illustrative, not measured data: the point is the trend, not the exact numbers</div>

You have already lived the small end of this scale. This course builds
the exact method that survives all the way to the large end.

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we solve many linked equations at once, exactly, without guessing?"</div>

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

1. Translate a real scaling problem into a system of linear equations
2. Use row operations to reduce a system to echelon form
3. Classify a system's solution set as exactly one solution, infinitely many, or none
4. State this course's four official objectives and where each is covered

---

# This Course's Four Objectives

<div class="thread">Not just this week's goals. This is what the syllabus commits this whole course to.</div>

| # | Objective (from the syllabus) | Where |
|---|---|---|
| 1 | Solve linear systems and perform matrix algebra, including inverses and factorizations | Weeks 1-2, 4-5 |
| 2 | Compute and interpret determinants and apply their properties | Week 6 |
| 3 | Verify vector space properties and determine bases, dimension, rank, coordinates | Weeks 7, 9 |
| 4 | Compute eigenvalues and eigenvectors and diagonalize matrices | Weeks 10-11 |

Weeks 12-14 (orthogonality, projections, least squares) apply all four
objectives together to the course's final, most practical payoff:
fitting a line to real, noisy data.

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who solved this exact problem, centuries ago?</div>

---

<!-- SLOT 8: Origin -->

# This Problem Is Not New

<div class="thread">You just felt the pain. Now: who else felt it, and what did they do about it?</div>

- **~200 BCE:** the Chinese mathematical text *The Nine Chapters on the Mathematical Art* already describes a systematic elimination method for solving several linked equations at once, arranged in a grid of numbers, centuries before algebra as we write it today existed
- **Early 1800s:** Carl Friedrich Gauss formalizes and popularizes the same elimination idea in the West while solving a very different real problem: predicting the orbit of the newly discovered dwarf planet Ceres from a handful of noisy telescope observations

<div class="why">
Gauss's astronomy problem is, underneath the telescope, the exact same
shape as the barista's recipe problem: several linked unknowns, several
observed constraints, one systematic method to solve them together
instead of guessing one at a time.
</div>

---

# Two Thousand Years, One Method

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">~200 BCE</div><div class="d">The Nine Chapters<br>elimination by grid of numbers</div></div>
<div class="pt"><div class="dot"></div><div class="y">1809</div><div class="d">Gauss, Ceres' orbit<br>elimination formalized</div></div>
<div class="pt"><div class="dot"></div><div class="y">1950s</div><div class="d">Digital computers<br>elimination, automated</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">GPS, graphics, machine learning<br>the same method, at massive scale</div></div>
</div>

The method survived two thousand years and a change from stone tablets
to supercomputers because the underlying problem, several linked
unknowns, never went away.

---

<!-- SLOT 9: Core concept -->

# Linear Equation & System: Definition

<div class="thread">Two thousand years of practice point at one precise definition. Here it is.</div>

> A **linear equation** in variables x₁, x₂, ..., xₙ can be written
> a₁x₁ + a₂x₂ + ... + aₙxₙ = b, where every variable appears only to the
> first power, never multiplied together, never inside a function.
>
> A **system of linear equations** is a collection of such equations,
> considered together, sharing the same variables.

- A **solution** is an assignment of values to every variable that makes every equation in the system true at once
- The **solution set** is the collection of all such solutions, which this week's method finds exactly

---

<!-- Act 3 / BUILD -->

# What Makes an Equation Linear

<div class="thread">The definition just given draws a sharp line. Here is exactly where it falls.</div>

| Linear | Not linear |
|---|---|
| 2x + 3y = 5 | x² + y = 5 (x is squared) |
| x - y + z = 0 | xy = 4 (variables multiplied together) |
| 0.5a + 2b - c = 10 | sin(x) + y = 1 (variable inside a function) |

Only linear equations are covered this semester. The "linear" in the
course's name is exactly this restriction, and it is precisely what
makes elimination always work the same predictable way.

---

# The Three Moves That Never Change a Solution

<div class="thread">One tool does all the work this week: three legal moves, applied one at a time.</div>

1. **Swap** two equations (their order never mattered)
2. **Scale** one equation by a nonzero number (both sides equally)
3. **Add** a multiple of one equation to another

These three "row operations" are the entire method. Applied carefully
and repeatedly, they turn a tangled system into one that can be read off
directly, top to bottom.

---

# From Equations to a Grid of Numbers

<div class="thread">Writing every variable name, every time, is slow. Here is the shortcut Gauss and the Nine Chapters both landed on.</div>

The system on the left and the augmented matrix on the right carry
exactly the same information, one written in words, one in position:

| System | Augmented matrix |
|---|---|
| 2x + y = 8 | `[ 2  1 | 8 ]` |
| x - y = 1 | `[ 1 -1 | 1 ]` |

Row operations on the grid are exactly the moves from the previous
slide, just faster to write and easier to automate on a computer.

---

# Demo, Step by Step: Solving the Café's Recipe

<div class="thread">Four steps, the exact system behind the wasted batches, solved for real.</div>

**Step 1 of 4: Write the recipe as equations.**

One cup uses `e` shots of espresso, `m` units of milk, `s` units of
syrup. Three known facts, from the original one-cup recipe and two
trial batches that tasted right: `e + m + s = 4`, `2e - m = 1`,
`m - s = -1`.

---

# Demo, Step by Step: Solving the Café's Recipe

**Step 2 of 4: Eliminate one variable at a time.**

From `2e - m = 1`: `m = 2e - 1`. Substitute into the other two
equations, leaving two equations in `e` and `s` only. This is row
reduction, done by substitution instead of the grid, same three moves
underneath.

---

# Demo, Step by Step: Solving the Café's Recipe

**Step 3 of 4: Solve the reduced system.**

The two-variable system reduces further to a single equation in one
unknown. Solving it gives `e = 1`, then back-substituting gives
`m = 1` and `s = 2`.

---

# Demo, Step by Step: Solving the Café's Recipe

**Step 4 of 4: Check, then scale exactly.**

Check: `1 + 1 + 2 = 4`. Correct. For 200 cups, multiply every one of
`e = 1, m = 1, s = 2` by 200: exactly `200, 200, 400`, no guessing, no
wasted batch. The barista's whole shift of trial and error collapses
into four lines of arithmetic.

---

# Three Possible Outcomes, Not Just One

<div class="thread">The café's system happened to have exactly one answer. That is not guaranteed.</div>

| Outcome | What it looks like (2 variables) | Meaning |
|---|---|---|
| **Unique solution** | Two lines cross at one point | Exactly one answer, like the café's recipe |
| **Infinitely many** | The two equations describe the same line | Any point on that line works |
| **No solution** | Two parallel lines, never touching | The constraints contradict each other |

Row reduction always reveals which of these three cases you are in,
without needing to guess in advance.

---

# Where This Shows Up Around You

<div class="thread">One recipe, solved. Here is the same shape of problem in systems you already use.</div>

<div class="appgrid">
<div class="app"><div class="name">GPS navigation</div><div class="desc">your position solved from satellite signal equations</div></div>
<div class="app"><div class="name">Computer graphics</div><div class="desc">rotating and scaling images: Week 3's linear transformations</div></div>
<div class="app"><div class="name">Economics models</div><div class="desc">input-output tables balancing an entire economy</div></div>
<div class="app"><div class="name">Traffic and network flow</div><div class="desc">balancing flow in and out of every junction</div></div>
<div class="app"><div class="name">Machine learning</div><div class="desc">every model you train later starts as a linear system</div></div>
</div>

None of these apps show you "a system of equations." Every one of them
solves one, constantly, underneath.

---

# Common Mistakes

- **Applying a row operation to only part of a row:** every number in the row must be updated, not just the one you are trying to zero out
- **Assuming every system has exactly one solution:** always check for the other two outcomes before reporting an answer
- **Losing track of a sign while eliminating:** the single most common source of a wrong final answer; recheck by substituting your solution back into the original equations, as the café demo just did

---

# Check Yourself

1. Is `x² + 2y = 7` a linear equation? Why or why not?
2. A system reduces to the equation `0 = 5`. What does that tell you about its solution set?

---

# Answers

1. **No.** `x` is squared, which violates the definition: every variable must appear only to the first power.
2. **No solution exists.** `0 = 5` is never true, so the constraints contradict each other, exactly the "parallel lines" case.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 2 slot 4 -->

# What Today's Method Cannot Do Yet

<div class="limits">
Row reduction solves any system exactly, by hand, for a small number of
variables. But writing out full equations, or even the augmented-matrix
grid, becomes unmanageable once a system has dozens or hundreds of
variables, which is the normal size for GPS, graphics, or machine
learning problems. We have a method. We do not yet have a compact way
to write it, or a way to hand it to a computer efficiently.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 1 leaves **a compact, computable way to represent a linear system**
unsolved. **Week 2, Vector and Matrix**, addresses it: writing any
system as `Ax = b`, the notation every later week and every real
application in this course builds on.

---

<!-- SLOT 16: Summary -->

# Summary

- A linear equation restricts every variable to the first power; a linear system is a collection of them sharing variables
- Three row operations, swap, scale, add, reduce any system to a form you can read off directly, without guessing
- A system has exactly one solution, infinitely many, or none, and row reduction always reveals which
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 1
- **Prepare:** find one real situation (not the café) where you scaled something by guessing, and bring it to Week 2

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
