---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 2: Vector & Matrix

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "Who found one real situation, not the café, where you
scaled something by guessing?" Take two quick answers before starting.
-->

---

<!-- SLOT 2: Where we are (Act 0 / LOCATE) -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk now"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
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

<!-- notes: One line: last week we solved by hand; this week we write it compactly. -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE) -->

# Last Week, This Week

- **Last week delivered:** how this course runs, how you're graded, and what's expected of you
- **Last week left broken:** there is still no way to find unknown amounts, like the café's fourth ingredient, without guessing

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), restates Week 1's Limit almost verbatim -->

# No Way to Write Unknowns Down Yet

<div class="pain">

We still do not have a way to find unknown amounts, like the café's
fourth ingredient, without guessing. And even once we can, GPS,
graphics, and machine learning need dozens or hundreds of unknowns at
once. Writing out full equations, one symbol at a time, becomes too
slow at that size. We have no method yet, and no compact way to write
one down, or hand it to a computer.

</div>

<!-- notes: This is Week 1's closing slide, restated as this week's opening problem. Let it land before moving on. -->

---

<!-- SLOT 5: Cost of not knowing (Act 1 / MOTIVATE) -->

# What This Actually Costs

- Writing out many equations by hand invites copying mistakes
- A program cannot read "e + m + s = 4" as text. It needs numbers in a grid
- Every field that solves many equations needs one shared way to write them down
- Two people solving the same system by hand can write it two different ways, and disagree by accident

<div class="why">
<strong>In industry:</strong> every linear algebra library (NumPy,
MATLAB, spreadsheet formulas) stores a system as a matrix and a
vector, never as separate written equations. Interviews expect
Ax = b directly.
</div>

---

# Writing It Out vs. Writing Ax = b

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">3 unknowns, full equations</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 20%"></div></div>
  <div class="bar-value">a few lines, manageable</div>
</div>
<div class="bar-row">
  <div class="bar-label">20 unknowns, full equations</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 70%"></div></div>
  <div class="bar-value">a full page, error-prone</div>
</div>
<div class="bar-row">
  <div class="bar-label">20 unknowns, as Ax = b</div>
  <div class="bar-track"><div class="bar-fill risk-low" style="width: 15%"></div></div>
  <div class="bar-value">still one line</div>
</div>
</div>
<div class="bar-note">illustrative, not measured data</div>

Compact notation stays short. Full equations do not.

---

<!-- SLOT 6: Driving question (Act 1 / MOTIVATE) -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we write and solve any linear system in one compact, computable form?"</div>

---

<!-- Key Words for 차시 1 -->

# Key Words Today

<div class="thread">4 words you will hear all class. Learn them now.</div>

- **Vector:** an ordered list of numbers, written as a column
- **Matrix:** a rectangular grid of numbers, arranged in rows and columns
- **Entry (component):** one single number inside a vector or matrix
- **Dimensions:** the size of a matrix, written as rows × columns

---

<!-- SLOT 7: Learning outcomes (Act 1 / MOTIVATE) -->

# By the End of This Week, You Can

<div class="cardlist">
<div class="card"><div class="h">Systems as <code>Ax = b</code></div><div class="d">Write any linear system as a vector, a matrix, and <code>Ax = b</code></div></div>
<div class="card"><div class="h">Matrix-Vector Multiplication</div><div class="d">Multiply a matrix by a vector, by hand</div></div>
<div class="card"><div class="h">Verify Solutions</div><div class="d">Verify a candidate solution using <code>Ax = b</code></div></div>
<div class="card"><div class="h">Row vs Column View</div><div class="d">Read <code>Ax</code> as separate rows, or as a mix of columns</div></div>
<div class="card"><div class="h">Compatibility Check</div><div class="d">Tell whether a matrix and vector are even compatible for multiplication</div></div>
</div>

---

# Coming Up: Writing the Café as Vectors

Next session, you turn the café's recipe rules into a vector, a
matrix, and one equation: `Ax = b`.

<div class="why">No new arithmetic. Just a faster way to write down what you already solved.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who invented this compact notation?</div>

---

<!-- Key Words for 차시 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Coefficient matrix:** the matrix built from a system's unknown coefficients, called `A`
- **Column vector:** a vector written top to bottom, one column
- **Matrix-vector product:** the result of multiplying a matrix by a vector
- **Ax = b:** the compact form of a linear system

---

<!-- SLOT 8: Origin (Act 2 / GROUND) -->

# Where This Idea Came From

<div class="thread">Same reason as always: many numbers, tracked as one object, beats separate symbols.</div>

- **1843-1844:** William Rowan Hamilton and Hermann Grassmann each describe a quantity with size and direction as one vector
- **1850s:** James Joseph Sylvester names the "matrix". Arthur Cayley defines how to add and multiply them as one object
- **Cayley's own reason:** he tracked transformation coefficients, and grew tired of writing them one at a time

<div class="why">
A grid of numbers is not new; Week 1's augmented matrix already used
one. What's new is treating the whole grid, and the whole column, as
one object with its own rules.
</div>

---

# From Elimination to One Line of Code

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">~200 BCE</div><div class="d">Nine Chapters<br>grid elimination</div></div>
<div class="pt"><div class="dot"></div><div class="y">1809</div><div class="d">Gauss<br>elimination formalized</div></div>
<div class="pt"><div class="dot"></div><div class="y">1843-1858</div><div class="d">Hamilton, Grassmann, Cayley<br>vector &amp; matrix notation</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Ax = b<br>one line, in every programming language</div></div>
</div>

One idea, four milestones: numbers, tracked together, solve linked
unknowns.

---

<!-- SLOT 9: Core concept (Act 2 / GROUND) -->

# Vector & Matrix: Definition

<div class="thread">Now the exact, formal definitions.</div>

> A **vector** is an ordered list of n numbers, written as a column
> with n entries.
>
> A **matrix** is a rectangular grid of numbers, arranged in rows and
> columns.

- A matrix's **dimensions** are rows × columns, e.g. a 3×3 matrix has 3 rows, 3 columns
- Bold capital letters name matrices, like `A`. Bold lowercase letters name vectors, like `x`
- A vector of all zeros is the **zero vector**; it still counts as a valid vector

---

<!-- Act 3 / BUILD -->

# Vector Operations: Scalar Multiply

<div class="thread">Two small operations vectors need, before we combine them with a matrix.</div>

Multiply every entry by the same number.

```
    [1]      [3]
3 * [2]  =   [6]
    [4]      [12]
```

---

# Vector Operations: Add

Add matching entries together.

```
[1]   [5]   [6]
[2] + [0] = [2]
[4]   [1]   [5]
```

---

# Vector Operations: Subtract

<div class="thread">Subtraction is nothing new: scale by -1, then add.</div>

```
[5]   [1]   [4]
[0] - [2] = [-2]
[1]   [4]   [-3]
```

Subtracting two vectors compares them, entry by entry - useful later
for checking how far a candidate answer is from the right one.

---

# The Café's Unknowns, as One Vector

<div class="thread">One column replaces three separate letters.</div>

Week 1's three unknowns become one vector, `x`:

```
    [ e ]
x = [ m ]
    [ s ]
```

Same espresso, milk, and syrup amounts. One object, not three.

---

# The Café's Three Rules, as One Matrix

Each row of matrix `A` holds one rule's coefficients, in order:

```
    [ 1  1  1 ]
A = [ 1  1 -1 ]
    [ 1 -1  0 ]
```

- Row 1: total liquid rule
- Row 2: syrup rule
- Row 3: equal-parts rule

---

# The Known Totals, as One Vector

`b` holds each rule's known total, in the same row order as `A`:

```
    [ 4 ]
b = [ 0 ]
    [ 0 ]
```

Row 1 of `A` pairs with row 1 of `b`, and so on.

---

# Ax = b: The Whole System, One Line

<div class="thread">Put the three pieces together.</div>

```
[ 1  1  1 ][ e ]   [ 4 ]
[ 1  1 -1 ][ m ] = [ 0 ]
[ 1 -1  0 ][ s ]   [ 0 ]
```

Same three café rules as Week 1. One compact line, ready for a
computer. A program only needs the three numbers `A`, `x`, `b`, not
the original sentences.

---

# Quick Recap: Three Objects, One Equation

| Object | What it holds | Café's version |
|---|---|---|
| `x` | The unknowns | `[e, m, s]` |
| `A` | The known coefficients | the 3×3 rule grid |
| `b` | The known totals | `[4, 0, 0]` |

`Ax = b` ties all three together, in one line.

---

# Reading the Rule: Row Times Column

<div class="thread">Before we check numbers, here is the general rule.</div>

```
[ a  b  c ][ x ]   [ ax + by + cz ]
[ d  e  f ][ y ] = [ dx + ey + fz ]
[ g  h  i ][ z ]   [ gx + hy + iz ]
```

Multiply each row's entries by the vector's entries, in order. Then
add.

---

# Reading A's Columns: What Each One Means

<div class="thread">Rows are not the only structure worth reading.</div>

In the café's matrix, each **column** belongs to one ingredient:

```
    [ 1  1  1 ]
A = [ 1  1 -1 ]
    [ 1 -1  0 ]
```

Column 1 is espresso's coefficients across all three rules; column 2
is milk's; column 3 is syrup's. Row view reads rules. Column view
reads ingredients.

---

# Not Every Matrix Is Square

<div class="thread">The café's `A` happens to be 3×3. That will not always be true.</div>

- The café's system has 3 rules and 3 unknowns: a **square** matrix, same number of rows and columns
- Other systems have more rules than unknowns, or fewer
- A non-square `A` still fits `Ax = b`; whether it has a solution is next week's question

---

# Building Ax = b From a Word Problem

<div class="thread">The café is one example. The method works on any word problem.</div>

A fruit stand sells apples and bananas. Two apples and one banana
cost 2400 원. One apple and three bananas cost 2700 원.

```
A = [ 2  1 ]      x = [ a ]      b = [ 2400 ]
    [ 1  3 ]          [ b ]          [ 2700 ]
```

Same three steps every time: name the unknowns, read off each rule's
coefficients into a row of `A`, and read off each rule's total into `b`.

---

# A Fourth Ingredient: Setting Up the Vector

<div class="thread">Week 1 left this unsolved: a regular drink, plus vanilla syrup.</div>

Add a fourth unknown, `v`, for vanilla syrup. The unknown vector grows
from three entries to four:

```
    [ e ]
x = [ m ]
    [ s ]
    [ v ]
```

Same idea as this week's three-ingredient vector. One more entry, no
new rule needed to write it down.

---

# A Fourth Ingredient: Building the Matrix

The café adds one new rule for vanilla syrup, alongside its original
three. Each row still holds one rule's coefficients, now with four
entries:

```
    [ 1  1  1  1 ]
A = [ 1  1 -1  0 ]
    [ 1 -1  0  0 ]
    [ 0  0  1 -1 ]
```

Rows 1-3 are the original three rules, extended with a zero for
vanilla where it does not appear. Row 4 is the new vanilla rule: the
syrup amount is one unit more than the vanilla amount.

---

# A Fourth Ingredient: The Totals Vector

`b` grows to four entries too, one total per rule, in the same order:

```
    [ 5 ]
b = [ 0 ]
    [ 0 ]
    [ 1 ]
```

The total liquid rule's target grows from 4 to 5, to make room for
the new ingredient. The other totals stay as before.

---

# A Fourth Ingredient: Ax = b, Assembled & Verified

<div class="thread">Verify a candidate answer, the same skill from this week's outcomes - just at a bigger size.</div>

Candidate answer: `e = 1, m = 1, s = 2, v = 1`. Multiply each row of
the 4×4 `A` by `x`, and compare to `b`:

```
Row 1: 1+1+2+1 = 5      Row 2: 1+1-2   = 0
Row 3: 1-1       = 0      Row 4: 2-1     = 1
```

All four rows match `b` exactly. Four unknowns, one compact equation,
verified the same way as three - this is Week 1's cliffhanger, closed.

---

<!-- SLOT N-2: Worked example, continues the running case study -->

# Case Study: Verify the Café's Solution (1/4)

<div class="thread">The café's solution is e = 1, m = 1, s = 2. Check it with Ax = b.</div>

Multiply row 1 of `A` by `x`, then compare to row 1 of `b`:

```
Row 1: 1(1) + 1(1) + 1(2) = 4
```

`b`'s first entry is also `4`. Row 1 checks out.

---

# Case Study: Verify the Café's Solution (2/4)

Multiply row 2 of `A` by `x`:

```
Row 2: 1(1) + 1(1) - 1(2) = 0
```

`b`'s second entry is `0`. Row 2 checks out.

---

# Case Study: Verify the Café's Solution (3/4)

Multiply row 3 of `A` by `x`:

```
Row 3: 1(1) - 1(1) + 0(2) = 0
```

`b`'s third entry is `0`. Row 3 checks out.

---

# Case Study: Verify the Café's Solution (4/4)

All three rows match. Stack the results back into one vector:

```
Ax = [ 4 ]      b = [ 4 ]
     [ 0 ]          [ 0 ]
     [ 0 ]          [ 0 ]
```

`Ax` equals `b` exactly. One multiplication replaced three separate
checks.

<!-- notes: Point out this is the same numeric answer as Week 1's café demo, only reached and checked differently. -->

---

# Case Study: A Wrong Candidate Solution

<div class="thread">Verification also catches a wrong answer - that's the whole point of doing it.</div>

Try `e = 1, m = 2, s = 1` instead. Multiply row 1 of `A` by this `x`:

```
Row 1: 1(1) + 1(2) + 1(1) = 4
```

Row 1 still matches `b`'s first entry, 4. But check row 3:

```
Row 3: 1(1) - 1(2) + 0(1) = -1
```

`b`'s third entry is `0`, not `-1`. Row 3 fails. This candidate is not
a solution - one failing row is enough to reject it.

---

# Multiplying by the Zero Vector

<div class="thread">One special input worth knowing, before moving on.</div>

Multiply the café's matrix `A` by the zero vector:

```
[ 1  1  1 ]   [ 0 ]   [ 0 ]
[ 1  1 -1 ] × [ 0 ] = [ 0 ]
[ 1 -1  0 ]   [ 0 ]   [ 0 ]
```

Any matrix times the zero vector gives the zero vector. This is why
`x = 0` is never an interesting candidate solution unless `b` is also
all zeros.

---

<!-- Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week02/worksheet.html">Worksheet Part A</a>.</div>

Write last week's Latte and Mocha system as `A`, `x`, and `b`.

Then multiply to verify the prices you already found.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to try the multiplication the other order (x times A) and see it does not fit. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: two ways to read the same multiplication.</div>

---

<!-- Key Words for 차시 3 -->

# Key Words Today

<div class="thread">4 words for the last part of this week.</div>

- **Linear combination:** adding scaled copies of vectors together
- **Compatible sizes:** a matrix's column count must match the vector's entry count
- **Row view / column view:** two ways to read the same matrix-vector product
- **Verify:** check an answer by computing `Ax` and comparing it to `b`

---

# Two Ways to Read Ax

<div class="thread">Same multiplication, two useful pictures.</div>

- **Row view:** each row of `A` times `x` gives one rule's answer, what we just did
- **Column view:** `Ax` is also a mix of `A`'s columns, scaled by `x`'s entries

```
      [1]        [ 1]        [ 1]
Ax =  e[1]   +   m[ 1]   +   s[-1]
      [1]        [-1]        [ 0]
```

Same answer either way. Column view returns in Week 3.

---

# Row View vs Column View: Café Recheck

<div class="thread">Apply the column view to the café's own numbers, and check it lands on the same answer as the row view.</div>

Using `e = 1, m = 1, s = 2`, scale each column of `A` and add:

```
    [1]        [ 1]        [ 1]     [ 4]
1 × [1]   +  1 [ 1]   +  2 [-1]  =  [ 0]
    [1]        [-1]        [ 0]     [ 0]
```

Same result as multiplying row by row. Row view and column view are
two roads to the same `Ax`.

---

# Compatible Sizes: When Ax Makes Sense

<div class="thread">One more rule before common mistakes.</div>

A matrix with `m` rows and `n` columns can multiply a vector with
exactly `n` entries. The result has `m` entries.

```
A is 2 x 3      x has 3 entries      Ax has 2 entries
```

If the vector's entry count does not match `A`'s column count, the
product is undefined.

---

# Compatible Sizes: A Worked Example

<div class="thread">See the size rule fail, on purpose, so you recognize it later.</div>

`A` is 2×3. Try to multiply it by a vector with only 2 entries:

```
A is 2 x 3      x has 2 entries      undefined
```

`A` has 3 columns, but `x` has only 2 entries - they do not match, so
`Ax` does not exist. Adding a third entry to `x` fixes it.

---

<!-- Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week02/worksheet.html">Worksheet Part B</a>.</div>

Check whether a candidate answer solves a 3-drink system.

Then test whether two given sizes can even be multiplied.

You have about 15 minutes.

---

# Try It: Quick Pair Check

<div class="why">Same pairs, no worksheet needed. Two minutes.</div>

Write down any 2×2 matrix and any 2-entry vector of your own. Swap
with your partner and compute their `Ax`, while they compute yours.

Compare answers. If you disagree, find the row that does not match.

---

# Quick Recap: Row vs Column View

| View | Reads `A` as | This week's example |
|---|---|---|
| Row view | one rule per row, matched to `x` | verifying the café's solution |
| Column view | one ingredient per column, scaled by `x` | the café recheck, a few slides back |

Same multiplication, same answer, two ways to picture it.

---

# Common Mistakes

<div class="cardlist">
<div class="card"><div class="h">Wrong multiplication order</div><div class="d">row times column, not column times row; order changes the answer's size</div></div>
<div class="card"><div class="h">Ignoring size mismatch</div><div class="d">`A`'s column count must equal `x`'s entry count, or the product is undefined</div></div>
<div class="card"><div class="h">Writing `b` as a row</div><div class="d">`b` must match `x`'s shape, a column vector</div></div>
<div class="card"><div class="h">Forgetting a sign when multiplying</div><div class="d">double-check each product before adding</div></div>
</div>

---

# Common Mistake: Wrong Order, Worked

<div class="thread">Seeing the mistake fail numerically sticks better than a rule alone.</div>

`A` is 2×3, `x` has 3 entries. `Ax` is defined and gives a 2-entry
result. Now try it backwards, `xA`: a 3-entry vector does not have 2
entries to match against `A`'s 2 rows. `xA` is not even defined here.

Always check which side the matrix sits on before multiplying.

---

# Common Mistake: Sign Errors, Worked

A row of `[1, -1, 0]` times `x = (1, 1, 2)` is easy to rush:

```
Wrong: 1 + 1 + 0 = 2
Right: 1(1) + (-1)(1) + 0(2) = 0
```

The minus sign belongs to the matrix entry, not the vector entry.
Carry every sign from `A` into the product, term by term.

---

# Common Mistake: Recomputing Habits

Recomputing `Ax` from scratch for every new candidate answer works,
but it hides a habit worth naming now: nothing about `A` changes
between candidates, only `x` does.

Week 5 turns this observation into a real shortcut. For now, just
notice it.

---

# Check Yourself

1. Write `2x + 3y = 5`, `x - y = 4` as `Ax = b`. What are `A` and `b`?
2. `A` is 2×3. Can it multiply a vector with 3 entries? What size is the answer?

---

# Answers

```
1. A = [  2   3 ]     b = [ 5 ]
       [  1  -1 ]         [ 4 ]
```

2. **Yes.** A 2×3 matrix times a 3-entry vector gives a 2-entry
   vector, one entry per row of `A`.

---

# Check Yourself: Round 2

3. The café adds a fourth ingredient, vanilla syrup, with `A` now
   4×4. Candidate answer `e=1, m=1, s=2, v=1`. Does row 4,
   `[0, 0, 1, -1]`, check out against `b`'s fourth entry, `1`?
4. Is `x = 0` ever a valid solution to `Ax = b`? When?

---

# Answers: Round 2

3. **Yes.** `0(1) + 0(1) + 1(2) - 1(1) = 1`, matching `b`'s fourth
   entry exactly.
4. **Only when `b` is also the zero vector.** Any matrix times the
   zero vector gives the zero vector, so it can never match a nonzero `b`.

---

<!-- Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week02/quiz.html">Week 2 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It
only shows you what you already know.

---

<!-- SLOT N+1: Limits (Act 4 / CLOSE), becomes Week 3 slot 4 -->

# What Ax = b Cannot Tell Us Yet

<div class="limits">
Ax = b organizes any system compactly, but nothing yet says whether a
solution even exists, or is unique.
</div>

---

<!-- SLOT N+2: Bridge -->

# Next Week

Week 2 leaves one thing unsolved: **whether Ax = b has a solution at
all, or exactly one.** **Week 3, Linear Transformation**, starts
answering this by treating `A` as an action on vectors, not just a
system to solve.

---

<!-- SLOT N+3: Summary -->

# Summary

- A vector is a column of numbers; a matrix is a grid of numbers, rows and columns
- Any linear system writes compactly as `Ax = b`
- Multiplying `Ax` checks a candidate solution in one operation, by row or by column
- A matrix's column count must match the vector's entry count, or the product is undefined
- **Reading:** Lay, Lay & McDonald, 6th ed., Sections 1.3-1.4
- **Handout:** [materials/week02/handout.md](materials/week02/handout.html), glossary and the full café walkthrough
- **Prepare:** bring one example, not the café, where "does a solution exist" actually matters

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
