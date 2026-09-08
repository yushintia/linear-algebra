---
marp: true
theme: shintia
paginate: true
math: katex
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 6: Determinants

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · Room 610
</div>

<!--
notes: Ask: "Before you fully solve a puzzle, can you tell if it even
has one answer?" That question is today's hook.
-->

---

<!-- SLOT 2: Where we are -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
<div class="wk"><div class="n">Wk 5</div><div class="t">Factorization</div></div>
<div class="wk now"><div class="n">Wk 6</div><div class="t">Determinants</div></div>
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

<!-- notes: One sentence: solve, represent, transform, compute, measure, approximate. We are now at "measure whether a solution is unique." -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE) -->

# Last Week, This Week

- **Last week delivered:** LU factorization sped up solving any linear system, by hand or by computer.
- **Last week left broken:** LU factorization speeds up solving, but tells us nothing about which directions in space a system actually reaches.

<!-- notes: This exact sentence is Week 5's Limit, restated almost verbatim. It becomes today's pain scenario. -->

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), ZERO jargon -->

# The Recipe Rule That Was Secretly Doubled

<div class="pain">

The Campus Café adds a fourth drink, the Mega Cup. Its recipe rule
looks brand new.

It is actually the old syrup rule, just doubled. Nobody notices this
at first.

The staff use last week's fast shortcut to work out exact amounts for
every drink's recipe. For most drinks, it works fine.

For the Mega Cup, the shortcut breaks halfway through. Numbers vanish
or blow up, and nobody can finish the calculation.

Nobody knew this recipe was trouble until they were already halfway
through work they could not use.

</div>

<!-- notes: Do not say "matrix," "determinant," or "singular" yet. Let the wasted half-finished work sit uncomfortably first. -->

---

# Checking Takes Seconds; Guessing Wastes the Whole Calculation

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">Check first, 2x2 recipe</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">a few seconds</div>
</div>
<div class="bar-row">
  <div class="bar-label">Check first, 3x3 recipe</div>
  <div class="bar-track"><div class="bar-fill risk-low" style="width: 25%"></div></div>
  <div class="bar-value">under a minute</div>
</div>
<div class="bar-row">
  <div class="bar-label">Skip the check, hit trouble mid-shortcut</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">the whole calculation, wasted</div>
</div>
</div>

The Mega Cup's trouble cost minutes. A larger recipe, skipped, costs
much more.

<!-- notes: Let the widening bars sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing (Act 1 / MOTIVATE) -->

# What This Actually Costs

- Wasted computation time, running a full shortcut on a recipe that was never going to give one clear answer
- A robot arm's control software can freeze mid-motion at a pose nobody checked in advance
- A building's support structure can hide a design flaw that only shows up as unsolvable equations

<div class="why">
<strong>In industry:</strong> engineers check a system for exactly this
kind of trouble before running expensive calculations, in robotics,
computer graphics, and structural design. "Does this system even have
one answer?" is a common technical interview question.
</div>

---

# This Check Scales; Guessing Does Not

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">3x3 recipe, by hand</div>
  <div class="bar-track"><div class="bar-fill risk-low" style="width: 20%"></div></div>
  <div class="bar-value">checked in under a minute</div>
</div>
<div class="bar-row">
  <div class="bar-label">Robot arm, 6 joints</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 55%"></div></div>
  <div class="bar-value">checked by computer, every move</div>
</div>
<div class="bar-row">
  <div class="bar-label">ML model, thousands of parameters</div>
  <div class="bar-track"><div class="bar-fill risk-high" style="width: 92%"></div></div>
  <div class="bar-value">needs the same check, automated</div>
</div>
</div>
<div class="bar-note">illustrative, not measured data</div>

You already met the small end of this problem. The same check runs at
every scale.

---

<!-- SLOT 6: Driving question (Act 1 / MOTIVATE) -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How can we tell, before fully solving, whether a system has exactly one answer?"</div>

---

<!-- Key Words for Session 1 -->

# Key Words Today

<div class="thread">4 words you will hear all class. Learn them now.</div>

- **Square matrix:** a grid of numbers with the same number of rows and columns, like 2x2 or 3x3
- **Determinant:** one number computed from a square matrix
- **Singular:** a system whose determinant is zero; not guaranteed to have one exact answer
- **Invertible:** the opposite of singular; guaranteed to have exactly one exact answer

---

<!-- SLOT 7: Learning outcomes (Act 1 / MOTIVATE) -->

# By the End of This Week, You Can

<div class="cardlist">
<div class="card"><div class="h">2x2 Determinants</div><div class="d">Compute the determinant of a 2x2 matrix</div></div>
<div class="card"><div class="h">3x3 Determinants</div><div class="d">Compute the determinant of a 3x3 matrix by cofactor expansion</div></div>
<div class="card"><div class="h">Determinants &amp; Solvability</div><div class="d">Use a determinant to decide if a system has exactly one solution</div></div>
<div class="card"><div class="h">Zero Determinant</div><div class="d">Explain what a zero determinant does, and does not, tell you</div></div>
</div>

---

<!-- preview hook, ends Session 1 -->

# Coming Up: Where This Idea Came From

Next session: who first solved this problem, centuries before
computers existed?

<div class="why">We will also meet the exact formula for a 2x2 determinant.</div>

---

<!-- Key Words for Session 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Minor:** the smaller grid left after removing one row and one column
- **Cofactor:** a minor's determinant, with a plus or minus sign attached
- **Sign pattern:** the plus/minus checkerboard used to assign each cofactor's sign
- **Expand along a row:** building a 3x3 determinant from smaller 2x2 pieces

---

<!-- SLOT 8: Origin (Act 2 / GROUND) -->

# Where This Idea Came From

<div class="thread">You just felt this pain. Others felt it too, centuries before you.</div>

- **1683, Japan:** Seki Takakazu writes down a determinant-like method for solving several equations together
- **1693, Germany:** Gottfried Leibniz uses the same idea independently, in a private letter about linear equations
- **1750, Switzerland:** Gabriel Cramer publishes a formula that reads a system's exact answer straight from its determinants

<div class="why">
Three mathematicians, three countries, no contact with each other.
The same problem kept forcing the same idea.
</div>

---

# From a Private Letter to a Named Idea

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1683</div><div class="d">Seki Takakazu, Japan<br>early determinant-like method</div></div>
<div class="pt"><div class="dot"></div><div class="y">1693</div><div class="d">Leibniz, Germany<br>same idea, independent letter</div></div>
<div class="pt"><div class="dot"></div><div class="y">1750</div><div class="d">Cramer, Switzerland<br>a formula using determinants</div></div>
<div class="pt"><div class="dot"></div><div class="y">1812</div><div class="d">Cauchy, France<br>names it "determinant," builds the general theory</div></div>
</div>

The name is 129 years younger than the idea. The problem came first,
every time.

---

<!-- SLOT 9: Core concept (Act 2 / GROUND) -->

# Determinant: Definition

<div class="thread">Now the exact, formal definition.</div>

> The **determinant** of a square matrix is a single number computed
> from its entries. It is zero exactly when the matrix has no
> inverse, and its system has no single exact answer.

- For a 2x2 matrix, this number has one simple formula
- For a 3x3 matrix, we build it from smaller 2x2 pieces, one step at a time

---

<!-- Act 3 / BUILD -->

# The 2x2 Determinant Formula

<div class="thread">The smallest case first. Everything larger builds on this.</div>

For a matrix

$$
\begin{bmatrix} a & b \\ c & d \end{bmatrix}
$$

the determinant is

$$
\det = ad - bc
$$

Example: for $\begin{bmatrix} 3 & 2 \\ 1 & 4 \end{bmatrix}$, $\det = 3(4) - 2(1) = 10$.

---

# Geometric Meaning: Determinant as Area

<div class="thread">A 2x2 determinant is not just an abstract number.</div>

Treat a matrix's two rows (or columns) as two vectors drawn from the
origin. The determinant's size equals the area of the parallelogram
they form.

$$
A = \begin{bmatrix} 3 & 0 \\ 0 & 4 \end{bmatrix} \quad \text{rows } (3,0) \text{ and } (0,4) \text{ form a } 3\times 4 \text{ rectangle}
$$

$$
\det(A) = 3(4) - 0(0) = 12 \quad \text{(matches the rectangle's area)}
$$

---

# Geometric Meaning: Negative Determinant Flips Orientation

<div class="thread">A negative determinant is not an error. It is information.</div>

- **Positive determinant:** the two row vectors keep their natural, counter-clockwise order
- **Negative determinant:** the two row vectors have been flipped, clockwise instead

The *size* (absolute value) still gives the parallelogram's area
either way.

---

# One Number, Two Outcomes

<div class="thread">Why bother computing this number at all? Here is the payoff.</div>

- **Nonzero determinant:** the system has exactly one solution
- **Zero determinant:** the system does not have exactly one solution. It has none, or infinitely many

This check takes seconds. Fully solving the system can take much
longer.

---

# Determinant and Invertibility: Tying It Together

<div class="thread">Same fact, three different words for it.</div>

For a square matrix $A$, these three statements always agree:

- $\det(A)$ is nonzero
- $A$ is **invertible** (Week 4's word for "has an inverse")
- $Ax = b$ has exactly one solution, for any $b$

If any one of the three holds, all three hold. If any one fails, all
three fail.

---

# Cramer's Rule: A Formula, Not Always Practical

<div class="thread">The Swiss mathematician from the timeline left us more than a name.</div>

Cramer's Rule writes each unknown as one determinant divided by
another. It needs a nonzero determinant to work at all.

For a small system, it is a quick shortcut. For a large system, full
elimination is still faster in practice.

---

# Cramer's Rule: Explicit 2x2 Formula

<div class="thread">The formula behind last slide's claim, written out.</div>

For $Ax = b$ with $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$, replace one column of $A$ with
$b$ at a time:

$$
x = \frac{\det\begin{bmatrix} b & b \\ d & d \end{bmatrix}}{\det(A)} \qquad y = \frac{\det\begin{bmatrix} a & b \\ c & d \end{bmatrix}}{\det(A)}
$$

Each unknown is its own determinant, divided by $\det(A)$.

---

# Case Study: Two Café Drinks, Checked First

<div class="thread">The Latte and Mocha prices from Week 1's worksheet. This time, check first.</div>

Latte: $2m + s = 800$. Mocha: $m + 3s = 900$. As a matrix:

$$
\begin{bmatrix} 2 & 1 \\ 1 & 3 \end{bmatrix}
$$

$$
\det = 2(3) - 1(1) = 5
$$

`5` is nonzero. One exact price for milk and syrup exists, before we
even solve for it.

---

# Determinant Property: Row Swap Flips the Sign

<div class="thread">Three properties, before we scale up to 3x3. First: order matters.</div>

Swap the Latte and Mocha rows from the last slide:

$$
\begin{bmatrix} 1 & 3 \\ 2 & 1 \end{bmatrix}
$$

$$
\det = 1(1) - 3(2) = -5
$$

Same numbers, one row swap, and the sign flips: `5` becomes `-5`. The
size, `5`, stays the same either way.

---

# Determinant Property: Scaling a Row Scales the Determinant

<div class="thread">Second property: stretching one rule stretches the answer to match.</div>

Double the Latte row only:

$$
\begin{bmatrix} 4 & 2 \\ 1 & 3 \end{bmatrix}
$$

$$
\det = 4(3) - 2(1) = 10
$$

Doubling one row exactly doubles the determinant: `5` becomes `10`.
Scale a row by $k$, and the determinant scales by $k$ too.

---

# Determinant Property: Adding a Multiple of a Row Changes Nothing

<div class="thread">Third property: this is why row reduction is safe.</div>

Add 2 times the Mocha row to the Latte row:

$$
\begin{bmatrix} 4 & 7 \\ 1 & 3 \end{bmatrix} \quad (\text{row}_1 + 2\cdot\text{row}_2)
$$

$$
\det = 4(3) - 7(1) = 5
$$

Still `5`, unchanged. This is exactly the row operation elimination
uses, which is why row-reducing a matrix never changes its
determinant.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week06/worksheet.html">Worksheet Part A</a>.</div>

Three new drink pairs. Three 2x2 matrices.

Compute each determinant first. Only solve the ones that pass.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. Confirm they check the determinant before attempting to solve any pair. -->

---

<!-- Key Words for Session 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Row swap:** swapping two rows flips the determinant's sign
- **Duplicate row:** two identical rows, or one a scaled copy of the other, make the determinant exactly zero
- **Scaled row:** multiplying one row by a number multiplies the whole determinant by that same number

---

# The 3x3 Determinant: Cofactor Expansion

<div class="thread">The same idea as 2x2, built from smaller pieces.</div>

For a 3x3 matrix, expand along the top row:

$$
\det = a_{11}C_{11} - a_{12}C_{12} + a_{13}C_{13}
$$

Each $C$ is the determinant of the 2x2 minor left after removing that
entry's row and column. Signs alternate: plus, minus, plus.

---

# Cofactor Sign Pattern, Visualized

<div class="thread">The plus/minus checkerboard, laid out fully for 3x3.</div>

$$
\begin{bmatrix} + & - & + \\ - & + & - \\ + & - & + \end{bmatrix}
$$

The sign for entry $(\text{row}, \text{column})$ is `+` when `row + column` is even,
`-` when it is odd. This checkerboard extends to any size matrix.

---

# Rule of Sarrus: A Shortcut for 3x3

<div class="thread">A second method, only for 3x3, no minors required.</div>

Copy the first two columns to the right of the matrix, then sum three
down-right diagonals and subtract three down-left diagonals:

$$
\left[\begin{array}{ccc|cc} a & b & c & a & b \\ d & e & f & d & e \\ g & h & i & g & h \end{array}\right]
$$

$$
\det = (aei + bfg + cdh) - (ceg + afh + bdi)
$$

Faster to write for 3x3, but it does **not** generalize to 4x4 or
larger. Cofactor expansion always does.

---

# Expanding Along a Different Row: Same Answer

<div class="thread">Cofactor expansion does not require the top row. Any row or column works.</div>

Expand the café's recipe matrix along row 2 instead of row 1:

$$
\begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & -1 \\ 1 & -1 & 0 \end{bmatrix}
$$

Row 2's signs are `-, +, -` (checkerboard). The expansion still
produces $\det = -4$, the same answer as expanding along row 1.

---

# Determinants Scale With the System

<div class="thread">3x3 is not the end. The same idea just keeps going.</div>

A 4x4 determinant expands into four 3x3 minors. A 4x4 minor expands
into 3x3 minors, and so on, one size smaller each time.

By hand, this gets slow fast. In practice, a computer runs this
expansion automatically, even for systems with hundreds of unknowns.

---

# Triangular Matrices: Determinant Is the Diagonal Product

<div class="thread">Week 5's `L` and `U` factors were triangular for a reason. Here it pays off again.</div>

For an upper or lower **triangular** matrix, one entry above or below
the diagonal does not matter. The determinant is just the product of
the diagonal entries:

$$
\begin{bmatrix} 2 & 1 & 4 \\ 0 & 3 & 5 \\ 0 & 0 & 1 \end{bmatrix} \;\Rightarrow\; \det = 2 \times 3 \times 1 = 6
$$

No cofactor expansion needed. This is why Week 5's $LU$ factorization
gives a fast way to compute a determinant, too: $\det(A) = \det(L) \times \det(U)$.

---

# Try It: Quick Property Check

<div class="why">In pairs, no full computation.</div>

For each pair below, decide the second determinant using only a
property from this session, not full recomputation:

1. $\det\begin{bmatrix}2 & 1\\ 1 & 3\end{bmatrix} = 5$. What is $\det\begin{bmatrix}1 & 3\\ 2 & 1\end{bmatrix}$?
2. A 3x3 triangular matrix has diagonal entries `2, -1, 4`. What is its determinant?

You have about 5 minutes.

---

# Demo, Step by Step: The Café's Recipe (1/4)

<div class="thread">Week 1's three-ingredient recipe. This time we check it, before solving it.</div>

The espresso-milk-syrup system from Week 1, as a matrix:

$$
\begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & -1 \\ 1 & -1 & 0 \end{bmatrix}
$$

Expand along the top row. Three 2x2 minors appear, one per entry.

---

# Demo, Step by Step: The Café's Recipe (2/4)

**Find each minor.** Cross out row 1 and one column at a time:

$$
\begin{aligned}
\text{minor for entry } (1,1): \begin{bmatrix} 1 & -1 \\ -1 & 0 \end{bmatrix} &\;\Rightarrow\; \det = (1)(0) - (-1)(-1) = -1 \\
\text{minor for entry } (1,2): \begin{bmatrix} 1 & -1 \\ 1 & 0 \end{bmatrix} &\;\Rightarrow\; \det = (1)(0) - (-1)(1) = 1 \\
\text{minor for entry } (1,3): \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix} &\;\Rightarrow\; \det = (1)(-1) - (1)(1) = -2
\end{aligned}
$$

---

# Demo, Step by Step: The Café's Recipe (3/4)

**Apply the sign pattern and sum.** Signs alternate plus, minus, plus:

$$
\begin{aligned}
\det &= (+1)(-1) - (1)(1) + (1)(-2) \\
\det &= -1 - 1 - 2 \\
\det &= -4
\end{aligned}
$$

---

# Demo, Step by Step: The Café's Recipe (4/4)

**Read the result.** $\det = -4$, which is nonzero.

This confirms what Week 1 found by full elimination: the recipe has
exactly one exact answer, $e = 1$, $m = 1$, $s = 2$.

The determinant told us this was coming, before we solved anything.

---

# Case Study: Row-Reduce the Café's Recipe First (1/3)

<div class="thread">A second, faster way to reach `det = -4`: row reduction instead of cofactor expansion.</div>

Start from the same recipe matrix. Add `-1` times row 1 to row 2, and
`-1` times row 1 to row 3 (no swap, no scaling, so the determinant is
unchanged):

$$
\begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & -1 \\ 1 & -1 & 0 \end{bmatrix} \;\Rightarrow\; \begin{bmatrix} 1 & 1 & 1 \\ 0 & 0 & -2 \\ 0 & -2 & -1 \end{bmatrix}
$$

---

# Case Study: Row-Reduce the Café's Recipe First (2/3)

The matrix is not yet triangular: row 2 and row 3 both have a nonzero
entry off the diagonal in an awkward spot. Swap rows 2 and 3 to fix
this (one swap, so the sign flips):

$$
\begin{bmatrix} 1 & 1 & 1 \\ 0 & -2 & -1 \\ 0 & 0 & -2 \end{bmatrix} \quad (\text{one row swap} \Rightarrow \text{sign flips})
$$

---

# Case Study: Row-Reduce the Café's Recipe First (3/3)

Now the matrix is triangular. Multiply the diagonal, then flip the
sign once, for the one row swap used:

$$
\begin{aligned}
\text{diagonal product} &= 1 \times (-2) \times (-2) = 4 \\
\text{one row swap} &\;\Rightarrow\; \det = -4
\end{aligned}
$$

Same answer as cofactor expansion: $\det = -4$. Row reduction and
cofactor expansion always agree, on any matrix.

---

# What a Zero Determinant Catches

<div class="thread">Back to today's pain. Here is why the Mega Cup broke.</div>

The Mega Cup's matrix has a doubled row:

$$
\begin{bmatrix} 1 & 1 & 1 \\ 2 & 2 & 2 \\ 1 & -1 & 0 \end{bmatrix}
$$

Row 2 is exactly row 1, scaled by 2. By the duplicate-row rule, its
determinant is exactly `0`, no calculation needed.

<div class="why">A determinant of 0 predicts the shortcut's failure, before anyone runs it.</div>

---

<!-- SLOT N-2: Worked example -->

# Case Study: Check Before You Solve

<div class="thread">Two combos, checked the same way, before spending any time solving.</div>

| Combo | Determinant | Meaning |
|---|---|---|
| Latte + Mocha (2x2) | `5`, nonzero | Exactly one price for milk and syrup |
| Café's 3-ingredient recipe (3x3) | `-4`, nonzero | Exactly one exact answer |
| Mega Cup (3x3) | `0` | Not one exact answer; do not run the full shortcut yet |

A 5-second check on the Mega Cup would have saved the wasted half-finished work from today's pain scenario.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week06/worksheet.html">Worksheet Part B</a>.</div>

Practice cofactor expansion on a 3x3 recipe matrix.

Then classify 3 small systems using only their determinant's sign and
value.

You have about 15 minutes.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

- **Losing the sign pattern:** the plus/minus checkerboard is easy to skip; a missed sign flips the whole answer
- **Mixing up rows and columns:** a minor removes one row *and* one column, matched to the entry's own position
- **Assuming zero always means "no solution":** it only rules out a unique answer. It does not say whether the system has none, or infinitely many

---

# More Common Mistakes

<div class="cardlist">
<div class="card"><div class="h">Forgetting a row swap's sign flip</div><div class="d">when row-reducing to compute a determinant, every swap flips the sign once</div></div>
<div class="card"><div class="h">det(A + B) ≠ det(A) + det(B)</div><div class="d">determinants do not distribute over addition; there is no shortcut here</div></div>
<div class="card"><div class="h">Using Sarrus on a 4x4 matrix</div><div class="d">the diagonal-copy trick only works for 3x3; larger matrices need cofactor expansion</div></div>
</div>

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Compute the determinant of $\begin{bmatrix}3 & 2\\ 1 & 4\end{bmatrix}$
2. A 3x3 system's matrix has determinant `0`. What does this tell you? What does it *not* tell you?

---

# Answers

1. $\det = 3(4) - 2(1) = 10$
2. **Tells you:** the system does not have exactly one solution. **Does not tell you:** whether it has none, or infinitely many; that needs more work to find out.

---

# Check Yourself: Properties

1. $\det\begin{bmatrix}5 & 2\\ 3 & 1\end{bmatrix} = -1$. Without recomputing, what is $\det\begin{bmatrix}3 & 1\\ 5 & 2\end{bmatrix}$?
2. A row of a 3x3 matrix is scaled by `-2`. Its determinant was `6`. What is it now?

---

# Answers

1. **`1`.** Swapping the two rows flips the sign of `-1`.
2. **`-12`.** Scaling one row by $k$ scales the whole determinant by $k$, and $6 \times (-2) = -12$.

---

# Check Yourself: Triangular Shortcut

1. A lower triangular matrix has diagonal entries `3, 0, 5`. What is its determinant, and what does that tell you about solving $Ax = b$?
2. Is $\det(A) = \det(A)$ after adding 3 times row 1 to row 3? Why or why not?

---

# Answers

1. **$\det = 3 \times 0 \times 5 = 0$.** The matrix is singular; $Ax = b$ does not have exactly one solution.
2. **Yes, unchanged.** Adding a multiple of one row to another never changes a determinant; this is the row operation elimination relies on.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week06/quiz.html">Week 6 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT N+1: Limits (Act 4 / CLOSE), becomes Week 7 slot 4 -->

# What a Determinant Cannot Do

<div class="limits">
A determinant tells us if a solution is unique, but not what the
whole space of solutions looks like. When the determinant is zero,
we know a unique answer does not exist. We still cannot describe what
the full set of possible answers actually is, or how large it is.
</div>

---

<!-- SLOT N+2: Bridge -->

# Next Week

Week 6 leaves one thing unsolved: **what the whole space of solutions
looks like, when it is not a single point.** **Week 7, Vector
Spaces**, addresses this.

---

<!-- SLOT N+3: Summary -->

# Summary

- A determinant is one number from a square matrix. It flags whether a system has exactly one exact answer
- 2x2: $\det = ad - bc$. 3x3: cofactor expansion, built from 2x2 minors, with alternating signs
- A zero determinant rules out a unique answer. It does not say whether the system has none or infinitely many
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 3
- **Handout:** [materials/week06/handout.md](materials/week06/handout.html), glossary and the full café determinant walkthrough
- **Prepare:** think of one situation where "not unique" means "many good answers," not "no answer." Bring it to Week 7

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
