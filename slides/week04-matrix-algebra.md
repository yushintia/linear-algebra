---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 4: Matrix Algebra

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "Have you ever had to redo the same two steps for every
single item on a list?" That doubled effort is today's hook.
-->

---

<!-- SLOT 2: Where we are -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk now"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
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

<!-- notes: One sentence: solve, represent, transform, compute, measure, approximate. We are moving from "transform" to "compute efficiently." -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE) -->

# Last Week, This Week

- **Last week delivered:** Week 3 wrote a single change, like a price
  adjustment, as one matrix.
- **Last week left broken:** it could not yet combine two changes into
  one, or undo a change that had already happened.

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE) -->

# One Change at a Time Is Not Enough

<div class="pain">

Last week, the Campus Café wrote one price change as a matrix: a
weekend discount. That worked. One change, one matrix.

This week, the café adds a second change: a delivery surcharge. Both
changes are matrices. But applying two matrices, one after another,
means solving the whole thing twice, for every single order.

Then a register glitch doubles every Saturday price by mistake. The
manager needs to undo just that one change exactly. Nothing so far
shows how to reverse a matrix.

We can describe one transformation as a matrix, but not yet combine or
reverse them.

</div>

<!-- notes: Let the "twice, for every order" line land before moving on. -->

---

# More Changes, More Work

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">1 change, applied once</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">last week's method works fine</div>
</div>
<div class="bar-row">
  <div class="bar-label">2 changes, discount then surcharge</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 55%"></div></div>
  <div class="bar-value">every order, redone twice</div>
</div>
<div class="bar-row">
  <div class="bar-label">4 changes: discount, surcharge, tax, loyalty</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">redone four times, every order</div>
</div>
</div>

Each new change multiplies the work. This course needs a way to do it
in one step.

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Redoing every order by hand doubles the work, and doubles the chance of a mistake
- A bigger café, with more daily rules, makes this worse with every new rule
- Without a way to reverse a change exactly, one mistake corrupts every order after it

<div class="why">
<strong>In industry:</strong> image and video editors combine crop,
rotate, and resize into one matrix instead of three slow passes. Game
engines and robots combine motions the same way. "Combine and undo
transformations efficiently" is a common technical interview question.
</div>

---

# Where Combine-and-Reverse Shows Up

<div class="thread">Same idea, many industries. This week's tool is not just for cafés.</div>

<div class="appgrid">
<div class="app"><div class="name">Graphics &amp; Games</div><div class="desc">Camera moves, rotations, and zooms combine into one matrix, once, per frame.</div></div>
<div class="app"><div class="name">Robotics</div><div class="desc">A robot arm combines every joint's rotation into one final position matrix.</div></div>
<div class="app"><div class="name">Software Undo</div><div class="desc">Many undo buttons work because the last action was invertible, so it can be reversed exactly.</div></div>
</div>

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we combine several changes into one step, and undo any one of them exactly?"</div>

---

<!-- NEW: Key Words for 차시 1 -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Matrix multiplication:** combining two matrices into one, using a fixed rule
- **Combine:** doing two changes as a single step
- **Inverse:** a matrix that undoes another matrix exactly
- **Identity matrix:** the "do nothing" matrix
- **Order:** the sequence changes happen in

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

<div class="cardlist">
<div class="card"><div class="h">Matrix Multiplication</div><div class="d">Multiply two matrices to combine two changes into one</div></div>
<div class="card"><div class="h">Non-Commutativity</div><div class="d">Explain why the order of multiplication changes the result</div></div>
<div class="card"><div class="h">Matrix Inverses</div><div class="d">Find a matrix's inverse and use it to undo a change exactly</div></div>
<div class="card"><div class="h">Singular Matrices</div><div class="d">Recognize when a matrix has no inverse</div></div>
</div>

---

<!-- NEW: preview hook, ends 차시 1 -->

# Coming Up: Worksheet Part A

Next session, you multiply matrices by hand.

Then you combine two real café price changes into a single matrix,
the same way a real checkout system applies several price rules at
once.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2: how two changes become one.</div>

---

<!-- NEW: Key Words for 차시 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Row-by-column:** the exact rule for multiplying two matrices
- **Dimensions:** a matrix's size, rows by columns
- **Square matrix:** a matrix with the same number of rows and columns
- **Commutative:** doing two things in either order gives the same result

---

<!-- SLOT 8: Origin -->

# Where This Idea Came From

<div class="thread">You just felt this pain. One mathematician felt it too, and named the fix.</div>

- **1858, England:** Arthur Cayley publishes *A Memoir on the Theory of Matrices*
- He was tracking what happens when one geometric change is followed by another
- Cayley defined a rule for "multiplying" two matrices so that it matched doing one change, then the other

<div class="why">
His rule also gave matrices an inverse: a way to undo a change, not
just describe it.
</div>

---

# From One Rule to Everyday Computing

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1858</div><div class="d">Cayley<br>defines matrix multiply &amp; inverse</div></div>
<div class="pt"><div class="dot"></div><div class="y">1950s</div><div class="d">Digital computers<br>automate matrix multiplication</div></div>
<div class="pt"><div class="dot"></div><div class="y">1990s</div><div class="d">3D graphics cards<br>chain matrices for every frame</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Deep learning<br>trillions of matrix multiplies, daily</div></div>
</div>

Combining changes into one matrix, then reversing them, is still the
same rule Cayley wrote down.

---

<!-- SLOT 9: Core concept -->

# Matrix Multiplication & Inverse: Definition

<div class="thread">Now the exact, formal definitions.</div>

> **Matrix multiplication** combines matrix `A` and matrix `B` into one
> matrix `AB`, applying `A`'s change, then `B`'s change, in one step.
>
> The **inverse** of a square matrix `A`, written `A⁻¹`, is the matrix
> that undoes `A` exactly.

- Applying `A` then `A⁻¹` (or `A⁻¹` then `A`) changes nothing
- Not every matrix has an inverse; this week teaches how to tell

---

<!-- Act 3 / BUILD -->

# Multiplying Two Matrices: The Rule

<div class="thread">One new rule does most of this week's work.</div>

Take each row of the first matrix, and each column of the second.
Multiply matching entries, then add.

```
A = [ 1  2 ]      B = [ 5  6 ]
    [ 3  4 ]          [ 7  8 ]

AB = [ 1×5+2×7   1×6+2×8 ]   [ 19  22 ]
     [ 3×5+4×7   3×6+4×8 ] = [ 43  50 ]
```

Row 1 of `A` meets column 1 of `B` for the top-left entry, and so on.

---

# Dimensions Must Match

<div class="thread">One rule decides if two matrices can even be multiplied.</div>

A matrix's size is rows × columns. To multiply `A` times `B`, the
number of columns in `A` must equal the number of rows in `B`.

```
A is 2 × 3, B is 3 × 2  →  AB is 2 × 2, this works
A is 2 × 3, B is 2 × 2  →  cannot multiply, 3 ≠ 2
```

Always check sizes first. A mismatch means the multiplication does not
exist at all.

---

# Order Matters: AB Is Not BA

<div class="thread">Numbers let you swap order freely. Matrices do not.</div>

```
A = [ 1  2 ]      B = [ 1  0 ]
    [ 0  1 ]          [ 3  1 ]

AB = [ 7  2 ]     BA = [ 1  2 ]
     [ 3  1 ]          [ 3  7 ]
```

`AB` and `BA` are different matrices. For matrices, order changes the
answer. Always multiply in the order the problem gives you. This is
why software applies a fixed, documented order for every change.

---

# The Identity Matrix: Doing Nothing

<div class="thread">One special matrix changes nothing at all.</div>

```
I = [ 1  0 ]
    [ 0  1 ]
```

Multiplying any matrix by `I` leaves it unchanged:

```
AI = A       IA = A
```

`I` plays the same role `1` plays in ordinary multiplication. Every
square matrix has its own identity matrix, always 1s down the
diagonal.

---

# The Inverse: Undoing a Matrix

<div class="thread">Now the tool this week has been missing: how to reverse a matrix.</div>

> A square matrix `A` has an **inverse** `A⁻¹` when

```
A × A⁻¹ = I       A⁻¹ × A = I
```

- Only a square matrix, same number of rows and columns, can have an inverse
- Not every square matrix has one; a matrix with no inverse is called **singular**

---

# Finding a 2×2 Inverse

<div class="thread">A short formula finds the inverse of any 2×2 matrix.</div>

```
For A = [ a  b ]      A⁻¹ = 1/(ad-bc) × [  d  -b ]
        [ c  d ]                        [ -c   a ]
```

This only works when `ad - bc` is not zero. Week 6 gives this number a
full name and method: the **determinant**.

```
A = [ 3  2 ]      ad-bc = 3×1 - 2×1 = 1
    [ 1  1 ]

A⁻¹ = [  1  -2 ]
      [ -1   3 ]
```

Check by multiplying `A × A⁻¹`. The result is `I`.

---

<!-- SLOT N-2: Worked example -->

# Case Study: Two Price Changes as Matrices

<div class="thread">Back to the café. Last week wrote one change as a matrix. Now there are two.</div>

Friday prices, Latte and Mocha, as a price vector:

```
p = [ 800 ]
    [ 900 ]
```

Weekend discount `D` (10% off Latte, 5% off Mocha):

```
D = [ 0.90   0   ]
    [  0    0.95 ]
```

Delivery surcharge `S` (adds 10% of the Latte price onto Mocha):

```
S = [ 1.00   0 ]
    [ 0.10   1 ]
```

---

# Case Study: Combining Them Into One Step

<div class="thread">Multiply the two matrices once. Reuse the result on every order.</div>

Multiply `S` and `D` to get one combined matrix `M`:

```
M = S × D = [ 0.90    0   ]
            [ 0.09   0.95 ]
```

Apply `M` to Friday's prices, in one step:

```
M × p = [ 720 ]
        [ 927 ]
```

Same answer as applying `D`, then `S`, separately. One multiplication
now replaces two full passes over every order.

---

# Case Study: Why Order Matters Here

<div class="thread">The café's rule is discount first, then surcharge. Swap it, and the price changes.</div>

```
S × D = [ 0.90    0   ]      D × S = [ 0.90    0    ]
        [ 0.09   0.95 ]              [ 0.095  0.95 ]
```

The two combined matrices are not the same. Applying the surcharge
first, then the discount, gives a slightly different final price.

The café's policy fixes the order: discount first, always. Matrix
order must match business order.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week04/worksheet.html">Worksheet Part A</a>.</div>

Multiply two small matrices by hand. Then combine two café price
changes into one matrix.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to check by applying the two original matrices separately and comparing. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: undoing a change, exactly.</div>

---

<!-- NEW: Key Words for 차시 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Invertible matrix:** a matrix that has an inverse
- **Singular matrix:** a matrix with no inverse
- **Verify:** check an answer by multiplying it back

---

# Using the Inverse to Undo a Mistake

<div class="thread">Now reverse a matrix. Undo the register glitch exactly.</div>

The register glitch doubled every Saturday price by mistake:

```
G = [ 2  0 ]      Saturday's wrong prices, G × p = [ 1600 ]
    [ 0  2 ]                                        [ 1800 ]
```

Find `G⁻¹` and apply it to undo the glitch exactly:

```
G⁻¹ = [ 0.5   0  ]     G⁻¹ × (G × p) = [ 800 ]
      [  0   0.5 ]                     [ 900 ]
```

Friday's correct prices are back, exactly, with no re-typing.

---

# The Inverse Also Solves Ax = b

<div class="thread">Week 1 solved this by hand. The inverse solves it in one line.</div>

Week 1's Latte and Mocha system, as a matrix equation:

```
A = [ 2  1 ]      x = [ m ]     b = [ 800 ]
    [ 1  3 ]          [ s ]         [ 900 ]
```

Instead of row reduction, multiply both sides by `A⁻¹`:

```
x = A⁻¹ b = [ 300 ]
            [ 200 ]
```

Same answer Week 1 found by hand: `m = 300`, `s = 200`.

---

# Not Every Matrix Can Be Undone

<div class="thread">One warning before you trust the inverse formula.</div>

```
A = [ 2  4 ]      ad - bc = 2×2 - 4×1 = 0
    [ 1  2 ]
```

`ad - bc = 0`, so `A⁻¹` does not exist. `A` is **singular**.

- This matches Week 1's "no unique solution" case: a singular matrix's system has none, or infinitely many, solutions
- Week 6's determinant gives an exact test for this, for any size matrix

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

<div class="cardlist">
<div class="card"><div class="h">Assuming AB = BA</div><div class="d">matrix order changes the answer; check the café's discount and surcharge example again</div></div>
<div class="card"><div class="h">Multiplying entry-by-entry</div><div class="d">matrix multiplication is row-by-column, not lining up matching spots</div></div>
<div class="card"><div class="h">Ignoring a size mismatch</div><div class="d">columns of the first matrix must match rows of the second; always check first</div></div>
<div class="card"><div class="h">Assuming every matrix has an inverse</div><div class="d">always check `ad - bc ≠ 0` before trusting `A⁻¹`</div></div>
</div>

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week04/worksheet.html">Worksheet Part B</a>.</div>

Find an inverse, then use it to solve a small system and undo a price
change.

You have about 15 minutes.

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. `A` is 2×3 and `B` is 3×4. What size is `AB`?
2. For `A = [[2,0],[0,3]]` and `B = [[1,1],[0,1]]`, is `AB` equal to `BA`?

---

# Answers

1. `AB` is 2×4. Its size is rows of `A` by columns of `B`.
2. **No.** `AB = [[2,2],[0,3]]`, but `BA = [[2,3],[0,3]]`. The top-right entry differs, so order matters here too.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week04/quiz.html">Week 4 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT N+1: Limits (Act 4 / CLOSE), becomes Week 5 slot 4 -->

# What Matrix Algebra Cannot Do Yet

<div class="limits">
We can multiply and invert matrices, but for large systems this is
still just slow arithmetic. Combining and reversing changes works, but
computing them by hand does not scale. A café with hundreds of orders
and dozens of rules needs a faster way to actually do this arithmetic,
not just a compact way to write it.
</div>

---

<!-- SLOT N+2: Bridge -->

# Next Week

Week 4 leaves one thing unsolved: **large systems are still slow to
compute by hand.** **Week 5, Factorization**, addresses it. It breaks a
matrix into simpler pieces that make solving much faster. This matters
most once a system has dozens, or hundreds, of unknowns.

---

<!-- SLOT N+3: Summary -->

# Summary

- Matrix multiplication combines two changes into one step; order changes the result
- A matrix's inverse undoes it exactly, and also solves `Ax = b` directly
- Not every matrix has an inverse; a matrix with `ad - bc = 0` is singular
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 2.1-2.3
- **Handout:** [materials/week04/handout.md](materials/week04/handout.html), glossary and the full café walkthrough
- **Reminder:** Assignment 1 is due this week
- **Prepare:** think of one time redoing a task twice felt slower than once. Bring it to Week 5

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
