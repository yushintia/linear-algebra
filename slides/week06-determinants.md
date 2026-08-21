---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 6: Determinants

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
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

<!-- Key Words for 차시 1 -->

# Key Words Today

<div class="thread">4 words you will hear all class. Learn them now.</div>

- **Square matrix:** a grid of numbers with the same number of rows and columns, like 2x2 or 3x3
- **Determinant:** one number computed from a square matrix
- **Singular:** a system whose determinant is zero; not guaranteed to have one exact answer
- **Invertible:** the opposite of singular; guaranteed to have exactly one exact answer

---

<!-- SLOT 7: Learning outcomes (Act 1 / MOTIVATE) -->

# By the End of This Week, You Can

1. Compute the determinant of a 2x2 matrix
2. Compute the determinant of a 3x3 matrix by cofactor expansion
3. Use a determinant to decide if a system has exactly one solution
4. Explain what a zero determinant does, and does not, tell you

---

<!-- preview hook, ends 차시 1 -->

# Coming Up: Where This Idea Came From

Next session: who first solved this problem, centuries before
computers existed?

<div class="why">We will also meet the exact formula for a 2x2 determinant.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with the history behind today's tool.</div>

---

<!-- Key Words for 차시 2 -->

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

```
[ a  b ]
[ c  d ]
```

the determinant is

```
det = ad - bc
```

Example: for `[[3, 2], [1, 4]]`, `det = 3(4) - 2(1) = 10`.

---

# One Number, Two Outcomes

<div class="thread">Why bother computing this number at all? Here is the payoff.</div>

- **Nonzero determinant:** the system has exactly one solution
- **Zero determinant:** the system does not have exactly one solution. It has none, or infinitely many

This check takes seconds. Fully solving the system can take much
longer.

---

# Cramer's Rule: A Formula, Not Always Practical

<div class="thread">The Swiss mathematician from the timeline left us more than a name.</div>

Cramer's Rule writes each unknown as one determinant divided by
another. It needs a nonzero determinant to work at all.

For a small system, it is a quick shortcut. For a large system, full
elimination is still faster in practice.

---

# Case Study: Two Café Drinks, Checked First

<div class="thread">The Latte and Mocha prices from Week 1's worksheet. This time, check first.</div>

Latte: `2m + s = 800`. Mocha: `m + 3s = 900`. As a matrix:

```
[ 2  1 ]
[ 1  3 ]
```

```
det = 2(3) - 1(1) = 5
```

`5` is nonzero. One exact price for milk and syrup exists, before we
even solve for it.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week06/worksheet.html">Worksheet Part A</a>.</div>

Three new drink pairs. Three 2x2 matrices.

Compute each determinant first. Only solve the ones that pass.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. Confirm they check the determinant before attempting to solve any pair. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: the same idea, for a bigger recipe.</div>

---

<!-- Key Words for 차시 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Row swap:** swapping two rows flips the determinant's sign
- **Duplicate row:** two identical rows, or one a scaled copy of the other, make the determinant exactly zero
- **Scaled row:** multiplying one row by a number multiplies the whole determinant by that same number

---

# The 3x3 Determinant: Cofactor Expansion

<div class="thread">The same idea as 2x2, built from smaller pieces.</div>

For a 3x3 matrix, expand along the top row:

```
det = a11*C11 - a12*C12 + a13*C13
```

Each `C` is the determinant of the 2x2 minor left after removing that
entry's row and column. Signs alternate: plus, minus, plus.

---

# Determinants Scale With the System

<div class="thread">3x3 is not the end. The same idea just keeps going.</div>

A 4x4 determinant expands into four 3x3 minors. A 4x4 minor expands
into 3x3 minors, and so on, one size smaller each time.

By hand, this gets slow fast. In practice, a computer runs this
expansion automatically, even for systems with hundreds of unknowns.

---

# Demo, Step by Step: The Café's Recipe (1/4)

<div class="thread">Week 1's three-ingredient recipe. This time we check it, before solving it.</div>

The espresso-milk-syrup system from Week 1, as a matrix:

```
[ 1   1   1 ]
[ 1   1  -1 ]
[ 1  -1   0 ]
```

Expand along the top row. Three 2x2 minors appear, one per entry.

---

# Demo, Step by Step: The Café's Recipe (2/4)

**Find each minor.** Cross out row 1 and one column at a time:

```
minor for entry (1,1): [ 1 -1 ; -1  0 ]  ->  det = (1)(0) - (-1)(-1) = -1
minor for entry (1,2): [ 1 -1 ;  1  0 ]  ->  det = (1)(0) - (-1)(1)  =  1
minor for entry (1,3): [ 1  1 ;  1 -1 ]  ->  det = (1)(-1) - (1)(1) = -2
```

---

# Demo, Step by Step: The Café's Recipe (3/4)

**Apply the sign pattern and sum.** Signs alternate plus, minus, plus:

```
det = (+1)(-1) - (1)(1) + (1)(-2)
det = -1 - 1 - 2
det = -4
```

---

# Demo, Step by Step: The Café's Recipe (4/4)

**Read the result.** `det = -4`, which is nonzero.

This confirms what Week 1 found by full elimination: the recipe has
exactly one exact answer, `e = 1`, `m = 1`, `s = 2`.

The determinant told us this was coming, before we solved anything.

---

# What a Zero Determinant Catches

<div class="thread">Back to today's pain. Here is why the Mega Cup broke.</div>

The Mega Cup's matrix has a doubled row:

```
[ 1   1   1 ]
[ 2   2   2 ]
[ 1  -1   0 ]
```

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

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Compute the determinant of `[[3, 2], [1, 4]]`
2. A 3x3 system's matrix has determinant `0`. What does this tell you? What does it *not* tell you?

---

# Answers

1. `det = 3(4) - 2(1) = 10`
2. **Tells you:** the system does not have exactly one solution. **Does not tell you:** whether it has none, or infinitely many; that needs more work to find out.

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
- 2x2: `det = ad - bc`. 3x3: cofactor expansion, built from 2x2 minors, with alternating signs
- A zero determinant rules out a unique answer. It does not say whether the system has none or infinitely many
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 3
- **Handout:** [materials/week06/handout.md](materials/week06/handout.html), glossary and the full café determinant walkthrough
- **Prepare:** think of one situation where "not unique" means "many good answers," not "no answer." Bring it to Week 7

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
