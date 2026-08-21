---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 15: Final Exam

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: This is a short review week, no new content (SPINE.md). Tell
students up front: today has no new concept, only Weeks 1-14,
consolidated before the final exam.
-->

---

<!-- SLOT 2: Where we are (Act 0 / LOCATE) -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
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
<div class="wk now review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: fourteen weeks built one growing toolkit. Today we step back and check every piece still works. -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE), reframed for a review
     week: no pain, no new gap, just where we stand -->

# Before the Final

- **Weeks 1-14 delivered:** solve, represent, transform, compute, measure, find special directions, and approximate. One growing toolkit
- **Today:** no new idea. We recap by theme, then practice with review questions
- **The final:** covers Weeks 1-14, worth 30% of your grade

---

<!-- Act 0 slot 3 expanded: plain-English recap, grouped by theme
     rather than 14 separate weeks -->

# Solve, Then Represent

<div class="thread">The semester's first move: turn a real problem into math, then solve it.</div>

- **Week 1:** row operations, swap, scale, add, solve any linear system exactly, by hand
- **Week 2:** the same system compacts into one form, `Ax = b`, ready for a computer
- Café link: three ingredient rules became one system, then one matrix equation

---

# Transform and Combine

<div class="thread">A matrix is not just numbers. It is a rule that moves every vector.</div>

- **Week 3:** any linear rule, scaling, rotation, reflection, shear, becomes one matrix
- **Week 4:** multiplying matrices combines two changes; an inverse undoes one exactly
- Café link: doubling every price by mistake, then undoing it with an inverse matrix

---

# Compute Efficiently

<div class="thread">Solving the same system's left side, over and over, wastes work.</div>

- **Week 5:** `LU` factorization splits `A` into two triangular pieces, just once
- Forward substitution, then back substitution, reuse that split for any new `b`
- Café link: one factorization solved many days of different receipts, instantly

---

# Measure the Solution Space

<div class="thread">Before solving fully, we learned to measure a system, not just solve it.</div>

- **Week 6:** a determinant flags whether a system has exactly one solution
- **Week 7:** vector spaces, span, and null space describe an entire solution set
- **Week 9:** a basis counts the truly independent directions; that count is the dimension

---

# Find Special Directions

<div class="thread">Some directions a matrix only stretches. Finding them pays off again and again.</div>

- **Week 10:** eigenvalues and eigenvectors solve `Av = λv`, the stretch-only directions
- **Week 11:** `A = PDP⁻¹` reuses those directions to make repeated transformations fast
- Café link: the loyalty-program blend settled toward one dominant eigenvalue direction

---

# Measure, Then Approximate

<div class="thread">The semester's last arc: measure exactly, then approximate what cannot be exact.</div>

- **Week 12:** the dot product measures length, distance, and angle between any two vectors
- **Week 13:** projection finds the closest point in a subspace, using orthogonality
- **Week 14:** least squares reuses projection to fit the best line through noisy data

---

<!-- Act 3 / BUILD slot, expanded per SPINE's short-review rule:
     "Check yourself" becomes the whole build act -->

<!-- _class: section -->

# Check Yourself: Weeks 1-14

<div class="driving-q">Fourteen questions, weighted toward Weeks 9-14. Answers follow each question.</div>

---

<!-- Q1: Week 1 -->

# Question 1 (Week 1)

<div class="thread">The two outcomes a system can reach besides "exactly one answer."</div>

After elimination, a café system reaches `0 = 5`. What does that tell
you about the solutions?

---

# Answer 1

**No solution.** `0 = 5` is never true, so the equations contradict
each other. No values can satisfy all of them together.

---

<!-- Q2: Week 2 -->

# Question 2 (Week 2)

Write `2x + 3y = 7`, `4x - y = 1` as `Ax = b`. What are `A` and `b`?

---

# Answer 2

```
A = [  2   3 ]     b = [ 7 ]
    [  4  -1 ]         [ 1 ]
```

---

<!-- Q3: Week 4 -->

# Question 3 (Week 4)

Find the inverse of `A = [[3,1],[2,1]]`.

---

# Answer 3

```
ad - bc = 3(1) - 1(2) = 1

A⁻¹ = [  1  -1 ]
      [ -2   3 ]
```

Check: `A · A⁻¹` gives the identity matrix, `[[1,0],[0,1]]`.

---

<!-- Q4: Week 5 -->

# Question 4 (Week 5)

`A = [[4,2],[2,3]]` factors as `L = [[1,0],[0.5,1]]`,
`U = [[4,2],[0,2]]`. Solve `Ax = b` for `b = [10, 9]`.

---

# Answer 4

Forward substitution, `Ly = b`:

```
y1 = 10
0.5(10) + y2 = 9   ->   y2 = 4
```

Back substitution, `Ux = y`:

```
2·x2 = 4          ->   x2 = 2
4·x1 + 2(2) = 10  ->   x1 = 1.5
```

---

<!-- Q5: Week 6 -->

# Question 5 (Week 6)

Compute the determinant of `A = [[1,0,2],[0,3,1],[1,1,1]]`.

---

# Answer 5

Cofactor expansion along row 1:

```
det = 1·det[[3,1],[1,1]] - 0 + 2·det[[0,3],[1,1]]
    = 1(3-1) - 0 + 2(0-3)
    = 2 - 6 = -4
```

Nonzero, so a system with this matrix has exactly one solution.

---

<!-- Q6: Week 7 -->

# Question 6 (Week 7)

The café's rule matrix `A` has a null space of dimension 2. What does
that tell you about solutions to `Ax = 0`?

---

# Answer 6

**Infinitely many.** A null space bigger than just the zero vector
means at least one unknown stays free, giving a whole family of
solutions, not just one.

---

<!-- Q7: Week 9 -->

# Question 7 (Week 9)

Are `v1 = (1,2,0)`, `v2 = (0,1,1)`, `v3 = (1,4,2)` linearly
independent?

---

# Answer 7

**No.** Try `v1 + 2v2`:

```
(1,2,0) + 2(0,1,1) = (1,4,2) = v3
```

`v3` is just `v1 + 2v2`, redundant. The set is dependent; only 2 of
the 3 vectors are truly independent.

---

<!-- Q8: Week 9 -->

# Question 8 (Week 9)

A 3×5 matrix has rank 3. What is its nullity?

---

# Answer 8

**Nullity = 2.** By rank-nullity, `rank + nullity = n`, the number of
columns:

```
3 + nullity = 5   ->   nullity = 2
```

---

<!-- Q9: Week 10 -->

# Question 9 (Week 10)

Find the eigenvalues of `A = [[4,2],[1,3]]`.

---

# Answer 9

```
det(A - λI) = (4-λ)(3-λ) - 2(1)
            = λ² - 7λ + 10 = 0
            = (λ - 5)(λ - 2) = 0
```

Eigenvalues: `λ = 5` and `λ = 2`.

---

<!-- Q10: Week 10 -->

# Question 10 (Week 10)

Find the eigenvector for `λ = 5`, from Question 9's matrix.

---

# Answer 10

Solve `(A - 5I)v = 0`:

```
[ -1   2 ] [v1]   [0]
[  1  -2 ] [v2] = [0]
```

Both rows give `v1 = 2v2`. Eigenvector: `(2, 1)`. Check:
`A(2,1) = (10,5) = 5(2,1)`. ✓

---

<!-- Q11: Week 11 -->

# Question 11 (Week 11)

Question 9's matrix has two different eigenvalues, `5` and `2`. Is it
diagonalizable? Why?

---

# Answer 11

**Yes.** Distinct eigenvalues always give independent eigenvectors.
Two independent eigenvectors are exactly enough to diagonalize any
2×2 matrix.

---

<!-- Q12: Week 12 -->

# Question 12 (Week 12)

Are `u = (3, -2)` and `v = (4, 6)` orthogonal? Show the dot product.

---

# Answer 12

```
u · v = 3(4) + (-2)(6) = 12 - 12 = 0
```

**Yes, orthogonal.** A dot product of zero always means a right
angle, in any number of dimensions.

---

<!-- Q13: Week 13 -->

# Question 13 (Week 13)

Project `y = (5, 3)` onto the line spanned by `u = (1, 0)`.

---

# Answer 13

```
proj_u(y) = ((y·u)/(u·u)) u
          = (5/1)(1, 0) = (5, 0)
```

The closest point on that line to `(5, 3)` is `(5, 0)`.

---

<!-- Q14: Week 14 -->

# Question 14 (Week 14)

A café survey collects 8 noisy taste ratings, but a line has only 2
unknowns. Why is there no exact solution to `Ax = b`?

---

# Answer 14

**More equations than unknowns.** With 8 data points and only 2
unknowns, `b` almost never lands exactly in the column space of `A`.
Least squares finds the closest fit instead.

---

<!-- SLOT N+1: "Limits" replaced by "What to focus on next" -->

# What to Focus On Next

<div class="limits">

- **Weeks 1-2:** rewrite one messy system as `Ax = b`, then solve it by row reduction, no notes
- **Weeks 3-5:** build a transformation matrix, invert it, then factor it into `LU`, all from scratch
- **Weeks 6-7, 9:** compute one determinant, describe a null space, then find a basis and its dimension
- **Weeks 10-11:** find eigenvalues and eigenvectors, then diagonalize, then check `A = PDP⁻¹` by hand
- **Weeks 12-14:** compute an angle, project a vector, then set up one least-squares fit end-to-end

</div>

---

<!-- SLOT N+2: Bridge -->

# After Today

Week 15 is review only; it carries no new limit forward. The final
exam covers Weeks 1-14, the same material recapped today.

You already have every tool this exam needs.

---

<!-- SLOT N+3: Summary -->

# Summary

- Fourteen weeks, one growing toolkit: solve, represent, transform, compute, measure, find special directions, approximate
- The same Campus Café recipe carried every week's example, start to finish
- The final exam covers Weeks 1-14. No new material appears on it
- **Reading:** re-read Lay, Lay & McDonald, 6th ed., Chapters 1-6
- **Prepare:** redo each week's Check Yourself questions without looking at the answers first

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
