---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 8: Midterm Review

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: This is a short review week, no new content (SPINE.md). Tell
students up front: today has no new concept, only Weeks 1-7,
consolidated before the midterm.
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
<div class="wk now review"><div class="n">Wk 8</div><div class="t">Midterm Exam</div></div>
<div class="wk"><div class="n">Wk 9</div><div class="t">Bases, Dimension</div></div>
<div class="wk"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: seven weeks built one growing toolkit. Today we
step back and check every piece still works. -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE), reframed for a review
     week: no pain, no new gap, just where we stand -->

# Before the Midterm

- **Weeks 1-7 delivered:** solve, represent, transform, combine, factor, measure, and describe. Seven skills, one running example
- **Today:** no new idea. We recap each week, then practice with review questions
- **The midterm:** covers Weeks 1-7 only, worth 30% of your grade

---

<!-- Act 0 slot 3 expanded: plain-English recap, one slide per week,
     each tied to that week's driving question -->

# Week 1: Linear Systems

<div class="thread">"How do we solve many linked equations at once, exactly, without guessing?"</div>

You should now be able to:

- Turn a real scaling problem into a system of equations
- Use row operations, swap, scale, add, to solve any system exactly
- Tell whether a system has one solution, many, or none

---

# Week 2: Vector & Matrix

<div class="thread">"How do we write and solve any linear system in one compact, computable form?"</div>

You should now be able to:

- Write any linear system as a vector, a matrix, and `Ax = b`
- Multiply a matrix by a vector, by hand
- Verify a candidate solution by computing `Ax` and comparing it to `b`

---

# Week 3: Linear Transformation

<div class="thread">"What does a matrix actually do to a vector, and how do we build one from a simple rule?"</div>

You should now be able to:

- Build a transformation matrix from a plain-English rule
- Recognize scaling, rotation, reflection, and shear from their matrices
- Tell whether a rule is a linear transformation, or not

---

# Week 4: Matrix Algebra

<div class="thread">"How do we combine several changes into one step, and undo any one of them exactly?"</div>

You should now be able to:

- Multiply two matrices to combine two changes into one
- Find a matrix's inverse and use it to undo a change exactly
- Recognize a singular matrix, one with no inverse

---

# Week 5: Factorization

<div class="thread">"If a system's left side never changes, can we solve it once and reuse that work forever?"</div>

You should now be able to:

- Factor a matrix `A` into a lower triangular `L` and an upper triangular `U`
- Solve a triangular system quickly, top to bottom or bottom to top
- Reuse one `LU` factorization to solve many systems sharing the same left side

---

# Week 6: Determinants

<div class="thread">"How can we tell, before fully solving, whether a system has exactly one answer?"</div>

You should now be able to:

- Compute the determinant of a 2x2 or 3x3 matrix
- Use a determinant to decide if a system has exactly one solution
- Explain what a zero determinant does, and does not, tell you

---

# Week 7: Vector Spaces

<div class="thread">"How do we describe an entire solution space, not just one solution?"</div>

You should now be able to:

- Check whether a set forms a vector space, or a subspace
- Find the span of a small set of vectors
- Describe the whole solution set of `Ax = 0` as a null space

---

<!-- Act 3 / BUILD slot, expanded per SPINE's short-review rule:
     "Check yourself" becomes the whole build act -->

<!-- _class: section -->

# Check Yourself: Weeks 1-7

<div class="driving-q">Ten questions. One from most weeks, two from the busier ones. Answers follow each question.</div>

---

<!-- Q1: Week 1 -->

# Question 1 (Week 1)

<div class="thread">The café's three rules, one more time.</div>

After elimination, two of the café's rules stay independent. The
third becomes `0 = 0`. What does that tell you about the solutions?

---

# Answer 1

**Infinitely many solutions.** `0 = 0` is always true, so one rule
added no new information. One unknown stays free.

---

<!-- Q2: Week 2 -->

# Question 2 (Week 2)

Write `3x - y = 5`, `2x + 4y = 6` as `Ax = b`. What are `A` and `b`?

---

# Answer 2

```
A = [  3  -1 ]     b = [ 5 ]
    [  2   4 ]         [ 6 ]
```

---

<!-- Q3: Week 3 -->

# Question 3 (Week 3)

A rule triples the x-coordinate and flips the sign of y. Write its
2x2 matrix.

---

# Answer 3

```
    [ 3   0 ]
A = [ 0  -1 ]
```

`T(1,0) = (3,0)` is column 1. `T(0,1) = (0,-1)` is column 2.

---

<!-- Q4: Week 4, multiplication -->

# Question 4 (Week 4)

Multiply `A = [[1,2],[3,1]]` and `B = [[2,0],[1,1]]`. Find `AB`.

---

# Answer 4

```
AB = [ 1(2)+2(1)   1(0)+2(1) ]   [ 4  2 ]
     [ 3(2)+1(1)   3(0)+1(1) ] = [ 7  1 ]
```

---

<!-- Q5: Week 4, inverse -->

# Question 5 (Week 4)

Recall Week 4's register glitch, `G = [[2,0],[0,2]]`. Find `G⁻¹`, and
say what it does.

---

# Answer 5

```
G⁻¹ = [ 0.5   0  ]
      [  0   0.5 ]
```

It undoes the doubling exactly, restoring the original prices.

---

<!-- Q6: Week 5 -->

# Question 6 (Week 5)

`A = [[2,1],[1,3]]` factors as `L = [[1,0],[0.5,1]]`,
`U = [[2,1],[0,2.5]]`. To solve `Ax = b` for `b = [800, 900]`, which
two steps do you take, in order?

---

# Answer 6

First solve `Ly = b` by forward substitution:

```
y = [ 800 ]
    [ 500 ]
```

Then solve `Ux = y` by back substitution: `s = 200`, `m = 300`. Same
answer as Week 1's Latte and Mocha worksheet.

---

<!-- Q7: Week 6, compute -->

# Question 7 (Week 6)

Compute the determinant of `[[4,1],[2,3]]`.

---

# Answer 7

```
det = 4(3) - 1(2) = 10
```

---

<!-- Q8: Week 6, meaning -->

# Question 8 (Week 6)

A 3x3 recipe matrix has determinant `0`. Does that mean no solution,
or could it mean many? Explain.

---

# Answer 8

**Cannot tell from the determinant alone.** Zero only rules out
exactly one solution. It could still be none, or infinitely many.
Row reduction tells you which.

---

<!-- Q9: Week 7, subspace test -->

# Question 9 (Week 7)

Does the set of all `(x, y, z)` with `x + y + z = 0` form a subspace
of R³? Why?

---

# Answer 9

**Yes.** It contains `(0, 0, 0)`. Adding or scaling any point that
sums to zero still sums to zero.

---

<!-- Q10: Week 7, null space / span, tied to case study -->

# Question 10 (Week 7)

The café's cheaper-drink rule is `2e + 4m - 2s = 0`, which gives
`e = -2m + s`. Write the full solution set as a span of two vectors.

---

# Answer 10

```
(e, m, s) = m(-2, 1, 0) + s(1, 0, 1)
```

This is the span of two vectors: the null space of the rule. Any `m`
and `s` gives one working recipe ratio.

---

<!-- SLOT N+1: "Limits" replaced by "What to focus on next" -->

# What to Focus On Next

<div class="limits">

<div class="cardlist">
<div class="card"><div class="h">Weeks 1-2</div><div class="d">practice row reduction and writing a system as `Ax = b`, until it feels automatic</div></div>
<div class="card"><div class="h">Weeks 3-4</div><div class="d">rebuild a transformation matrix from a rule, and check `AB ≠ BA` with your own example</div></div>
<div class="card"><div class="h">Week 5</div><div class="d">walk through one forward, then back, substitution from scratch, no notes</div></div>
<div class="card"><div class="h">Week 6</div><div class="d">compute one 3x3 determinant by cofactor expansion, fully by hand</div></div>
<div class="card"><div class="h">Week 7</div><div class="d">run the three-part subspace check on a set you have not seen before</div></div>
</div>

</div>

---

<!-- SLOT N+2: Bridge -->

# Next Week

Week 8 is review only; it carries no new limit forward. **Week 9,
Bases and Dimension**, picks up where Week 7 left off: measuring how
big a solution space actually is.

---

<!-- SLOT N+3: Summary -->

# Summary

- Seven weeks, one growing toolkit: solve, represent, transform, combine, factor, measure, describe
- The same Campus Café recipe carried every week's example, start to finish
- The midterm covers Weeks 1-7 only. No new material appears on it
- **Reading:** re-read Lay, Lay & McDonald, 6th ed., Chapters 1-4
- **Prepare:** redo each week's handout practice problems without looking at the answers first

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
