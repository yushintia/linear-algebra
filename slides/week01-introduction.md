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
notes: Ask: "Has anyone ever doubled a recipe and it came out wrong?"
That feeling is today's hook.
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

<!-- notes: One sentence: solve, represent, transform, compute, measure, approximate. 15 weeks, one growing toolkit. -->

---

<!-- NEW: warm-up, right after the roadmap (Simplification Rule 3) -->

# Before We Start

<div class="thread">A quick warm-up. This checks one math skill this course needs.</div>

Solve this equation. Find `x`.

## 3x = 12

Work alone for 1 minute. Then check your answer with a classmate.

<!--
notes: Give students 60 seconds of silence to solve 3x = 12 (answer: x = 4).
Then ask the class aloud, one question at a time:
1. "What number is x?"
2. "What operation did you use — divide or multiply?"
3. "Now try 5x = 20 in your head. What is x?"
Confirm most hands are up before moving on.
-->

---

<!-- SLOT 3: What you already bring -->

# What You Already Bring

No formal prerequisite is required for this course. But you already
know useful things:

- **High school algebra:** you have solved two equations with two unknowns before
- **Programming:** you already think in variables and operations; this course makes that idea formal
- **Basic arithmetic:** fractions and negative numbers, the only math skill this course assumes

This course does not teach new arithmetic. It teaches an exact way to
solve many equations at once, without guessing.

---

<!-- Course logistics appendix -->

<!-- _class: section -->

# Course Logistics
<div class="driving-q">Read once now. Use all semester.</div>

---

# Grading & Materials

| Item | Weight |
|---|---|
| Attendance | 10% |
| Midterm | 30% |
| Final | 30% |
| Assignments | 10% |
| In-class items | 20% |

<!-- notes: Assignment 1 due Week 4. Assignment 2 due Week 11. Quiz 1 Week 7. Quiz 2 Week 14. -->

---

# Textbook, Policy & Contact

- **Textbook:** Lay, Lay & McDonald, *Linear Algebra and Its Applications*, 6th ed., Pearson, 2020
- **References:** Hefferon, *Linear Algebra*, 4th ed. (open textbook); Cherney, Denton, Thomas & Waldron, *Linear Algebra*, UC Davis, 2013
- **Policy:** attend and take part every class; late assignments lose points; plagiarism and cheating lead to discipline
- **Contact:** yushintia@deu.ac.kr, office hours by email appointment

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# A Recipe That Goes Wrong

<div class="pain">

The Campus Café has one drink recipe: espresso, milk, and syrup. It
tastes right for one cup.

A professor books the café for a 200-person event. Same drink, same
taste, just more of it.

The barista multiplies every ingredient by 200. It does not work. One
batch is too sweet. One is too weak. One is too strong.

By the end of the shift, three large batches are poured down the
drain. The event still does not have enough of its drink.

</div>

<!-- notes: Do not say "equation" or "matrix" yet. Let the wasted batches sit uncomfortably first. -->

---

# Guessing Gets Worse as Numbers Grow

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">1 cup, by feel</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">usually fine</div>
</div>
<div class="bar-row">
  <div class="bar-label">10 cups, "just multiply"</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 45%"></div></div>
  <div class="bar-value">taste starts to drift</div>
</div>
<div class="bar-row">
  <div class="bar-label">200 cups, real order</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">three batches wasted</div>
</div>
</div>

Guessing does not scale. This course teaches a method that does.

<!-- notes: Let the widening bars sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Wasted ingredients waste money, every single time
- An engineer who cannot solve linked equations exactly may design something unsafe
- A map app that solves its position equations wrong sends you to the wrong street

<div class="why">
<strong>In industry:</strong> "set up and solve this system" sits behind
GPS, computer graphics, economic models, and every machine learning
model you meet later in this major. It is a common question in
technical job interviews.
</div>

---

# The Same Problem, Bigger Every Time

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">3 ingredients, 1 recipe</div>
  <div class="bar-track"><div class="bar-fill risk-low" style="width: 20%"></div></div>
  <div class="bar-value">solvable by hand</div>
</div>
<div class="bar-row">
  <div class="bar-label">GPS: 4 satellites</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 55%"></div></div>
  <div class="bar-value">solved by your phone, every second</div>
</div>
<div class="bar-row">
  <div class="bar-label">ML model: millions of unknowns</div>
  <div class="bar-track"><div class="bar-fill risk-high" style="width: 92%"></div></div>
  <div class="bar-value">needs a systematic method</div>
</div>
</div>
<div class="bar-note">illustrative, not measured data</div>

You already met the small end of this problem. This course builds the
method for the large end too.

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we solve many linked equations at once, exactly, without guessing?"</div>

---

<!-- NEW: Key Words for 차시 1 (Simplification Rule 2) -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Equation:** a math sentence with an equal sign, like `2x = 8`
- **Unknown (variable):** the letter we do not know yet, like `x`
- **Linear:** every unknown stands alone, never squared, never multiplied by another unknown
- **System:** two or more equations, solved together
- **Solution:** the value(s) that make every equation true at the same time

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

1. Turn a real scaling problem into a system of equations
2. Use row operations to simplify a system
3. Tell whether a system has one solution, many, or none
4. Name this course's four main objectives

---

# This Course's Four Objectives

<div class="thread">Not just this week's goal. This is the whole course's promise.</div>

| # | Objective (from the syllabus) | Where |
|---|---|---|
| 1 | Solve linear systems; find matrix inverses and factorizations | Weeks 1-2, 4-5 |
| 2 | Compute and use determinants | Week 6 |
| 3 | Find vector space properties, bases, and dimension | Weeks 7, 9 |
| 4 | Compute eigenvalues and diagonalize matrices | Weeks 10-11 |

Weeks 12-14 combine all four objectives: fitting a line to real, noisy
data, the final payoff of this course.

---

<!-- NEW: preview hook, ends 차시 1 (Simplification Rule 3 shape) -->

# Coming Up: Worksheet Part A

Next session, you solve a real Campus Café problem in pairs.

Two drinks. Two shared ingredients. You guess first, then use this
week's method.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who solved this exact problem, long ago?</div>

---

<!-- NEW: Key Words for 차시 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Row operation:** one of 3 legal moves that never changes the answer
- **Augmented matrix:** the equations written as a grid of numbers
- **Elimination:** removing one unknown at a time until you can solve directly
- **Solution set:** the full list of every correct answer

---

<!-- SLOT 8: Origin -->

# This Problem Is Not New

<div class="thread">You just felt this pain. Others felt it too, long before you.</div>

- **~200 BCE, China:** *The Nine Chapters on the Mathematical Art* already solves linked equations, using a grid of numbers
- **1809, Germany:** Carl Friedrich Gauss uses the same idea to predict a dwarf planet's orbit from a few noisy measurements

<div class="why">
Different problem, same shape: several unknowns, several known facts,
one systematic method instead of guessing one at a time.
</div>

---

# Two Thousand Years, One Method

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">~200 BCE</div><div class="d">The Nine Chapters<br>elimination by grid of numbers</div></div>
<div class="pt"><div class="dot"></div><div class="y">1809</div><div class="d">Gauss, Ceres' orbit<br>elimination formalized</div></div>
<div class="pt"><div class="dot"></div><div class="y">1950s</div><div class="d">Digital computers<br>elimination, automated</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">GPS, graphics, machine learning<br>the same method, at massive scale</div></div>
</div>

This method survived 2,000 years because the problem, many linked
unknowns, never went away.

---

<!-- SLOT 9: Core concept -->

# Linear Equation & System: Definition

<div class="thread">Now the exact, formal definition.</div>

> A **linear equation** in x₁, x₂, ..., xₙ has the form
> a₁x₁ + a₂x₂ + ... + aₙxₙ = b. Every unknown appears only once, to the
> first power.
>
> A **system of linear equations** is a group of such equations,
> sharing the same unknowns.

- A **solution** gives a value to every unknown that makes all equations true together
- The **solution set** is every possible solution; this week's method finds it exactly

---

<!-- Act 3 / BUILD -->

# What Makes an Equation Linear

<div class="thread">The definition just given draws a sharp line. Here it is.</div>

| Linear | Not linear |
|---|---|
| 2x + 3y = 5 | x² + y = 5 (x is squared) |
| x - y + z = 0 | xy = 4 (unknowns multiplied together) |
| 0.5a + 2b - c = 10 | sin(x) + y = 1 (unknown inside a function) |

Only linear equations are in this course. The word "linear" in the
course's name is exactly this rule.

---

# The Three Moves That Never Change a Solution

<div class="thread">One tool does all the work this week: three legal moves, one at a time.</div>

1. **Swap** two equations
2. **Scale** one equation by a nonzero number
3. **Add** a multiple of one equation to another

These three "row operations" are the whole method. Used carefully,
they turn a messy system into one you can read directly, top to
bottom.

---

# From Equations to a Grid of Numbers

<div class="thread">Writing every unknown, every time, is slow. Here is a faster way.</div>

The system on the left and the augmented matrix on the right hold the
same information, one in words, one in position:

| System | Augmented matrix |
|---|---|
| 2x + y = 8 | `[ 2  1 \| 8 ]` |
| x - y = 1 | `[ 1 -1 \| 1 ]` |

A row operation on the grid is the same move as before, just faster
to write and easier for a computer.

---

# Demo, Step by Step: Solving the Café's Recipe (Part 1)

<div class="thread">The exact system behind the wasted batches. Let's solve it for real.</div>

**Step 1: Turn the café's own rules into equations.**

One cup uses `e` shots espresso, `m` units milk, `s` units syrup:
`e + m + s = 4` (total liquid), `e + m - s = 0` (syrup = espresso +
milk), `e - m = 0` (equal espresso and milk).

**Step 2: Remove one unknown.**

From `e - m = 0`: `m = e`. Put this into the other two equations. Now
only `e` and `s` remain, in two equations.

<!-- notes: The Campus Café is invented; its numbers are picked to come
out even. Tell students this out loud here: the story is fictional,
the method is the real, general one they will use on any linear
system, all semester. -->

---

# Demo, Step by Step: Solving the Café's Recipe (Part 2)

**Step 3: Solve what is left.**

Substituting `m = e` gives `2e - s = 0` and `2e + s = 4`. Adding them
cancels `s`: `4e = 4`, so `e = 1`. Then `m = 1` and `s = 2`.

**Step 4: Check your answer.**

`1 + 1 + 2 = 4` ✓. `1 + 1 - 2 = 0` ✓. `1 - 1 = 0` ✓. All three café
rules hold. For 200 cups, multiply each number by 200: exactly
`200, 200, 400`. No guessing, no waste.

---

<!-- NEW: Try It, hands off to Worksheet Part A (Simplification Rule 4) -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open Worksheet Part A.</div>

Two drinks. Two shared ingredients. Two unknown prices.

First guess. Then use this week's row operations to solve exactly.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to check their answer by putting it back into both original equations. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: check your Worksheet A answer, then go further.</div>

---

<!-- NEW: Key Words for 차시 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Unique solution:** exactly one correct answer
- **Infinitely many solutions:** more than one correct answer, a whole family of them
- **No solution:** the equations contradict each other; nothing satisfies all of them

---

# Three Possible Outcomes, Not Just One

<div class="thread">The café's system had exactly one answer. That will not always happen.</div>

| Outcome | What it looks like (2 unknowns) | Meaning |
|---|---|---|
| **Unique solution** | Two lines cross at one point | Exactly one answer, like the café's recipe |
| **Infinitely many** | The two equations describe the same line | Any point on that line works |
| **No solution** | Two parallel lines, never touching | The equations contradict each other |

Row reduction always tells you which case you are in. You never have
to guess.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open Worksheet Part B.</div>

Check your Part A answer using the augmented matrix.

Then classify 3 small systems: one solution, many, or none.

You have about 15 minutes.

---

# Common Mistakes

- **Changing only part of a row:** every number in the row must change, not just the one you are zeroing out
- **Assuming one answer always exists:** always check for the other two cases first
- **Losing a sign while eliminating:** the most common cause of a wrong answer; always check by substituting back into the original equations

---

# Check Yourself

1. Is `x² + 2y = 7` linear? Why or why not?
2. A system reduces to `0 = 5`. What does that tell you about its solution set?

---

# Answers

1. **No.** `x` is squared. Every unknown must stay to the first power.
2. **No solution.** `0 = 5` is never true, so the equations contradict each other.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the Week 1 quiz. Answer alone, no notes.</div>

8 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 2 slot 4 -->

# What Today's Method Cannot Do Yet

<div class="limits">
Row reduction solves any system exactly, by hand. But it only works
well for a small number of unknowns. GPS, graphics, and machine
learning need dozens or hundreds of unknowns. Writing full equations,
or even the matrix grid, becomes too slow at that size. We have a
method. We do not yet have a compact way to write it, or hand it to a
computer.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 1 leaves one thing unsolved: **a compact, computable way to
write a linear system.** **Week 2, Vector and Matrix**, solves this.
It writes any system as `Ax = b`, the notation every later week
builds on.

---

<!-- SLOT 16: Summary -->

# Summary

- A linear equation keeps every unknown to the first power. A system is a group of them, sharing unknowns
- Three row operations, swap, scale, add, solve any system, without guessing
- A system has exactly one solution, infinitely many, or none. Row reduction always reveals which
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 1
- **Prepare:** find one real situation (not the café) where you scaled something by guessing, and bring it to Week 2

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
