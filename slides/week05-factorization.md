---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 5: Factorization

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "Have you ever redone the same homework problem, from scratch,
five days in a row?" That feeling is today's hook.
-->

---

<!-- SLOT 2: Where we are -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
<div class="wk now"><div class="n">Wk 5</div><div class="t">Factorization</div></div>
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

<!-- notes: One sentence: solve, represent, transform, compute, measure, approximate. Today we speed up "compute". -->

---

<!-- SLOT 3: Recap + open wound -->

# Last Week, This Week

- **Last week delivered:** Week 4 taught you to multiply matrices and find their inverses.
- **Last week left broken:** We can multiply and invert matrices, but for large systems this is still just slow arithmetic.

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# Same Two Drinks, Every Single Day

<div class="pain">

The Campus Café's Latte and Mocha never change. Two cups, two fixed
recipes, every single day.

But the price of milk and the price of syrup change almost daily.
Each morning, the manager checks yesterday's receipts and works out
today's prices, by hand, from a blank page.

She repeats every step from scratch: the same moves she used
yesterday, and the day before that.

Some weeks she adds a third drink. Now there are three prices to
find, not two. The work grows, and so does the time it takes, every
single morning.

</div>

<!-- notes: Do not say "matrix", "factor", or "invert" here. Let the repeated, wasted mornings sit uncomfortably first. -->

---

# Solving From Scratch Gets Old Fast

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">1 morning, 1 recipe check</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">quick enough</div>
</div>
<div class="bar-row">
  <div class="bar-label">1 work-week, same recipe, redone daily</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 55%"></div></div>
  <div class="bar-value">the same work, five times</div>
</div>
<div class="bar-row">
  <div class="bar-label">1 year, same recipe, redone daily</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">the same work, over 300 times</div>
</div>
</div>

Redoing the same work, every day, adds up fast. This week finds a
shortcut.

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Every morning spent re-solving the same problem is time not spent serving customers
- A business that resolves the same layout daily wastes real time, every single day
- Large simulations, like weather models, solve a similar-shaped system thousands of times in one run
- A scheduling system that recomputes routes from scratch, even when only the day's traffic changes, wastes computing time too

<div class="why">
<strong>In industry:</strong> engineers running crash simulations,
weather forecasts, and power-grid checks solve the same-shaped system
many times, with new data each time. Reusing prior work, instead of
restarting, is a common systems-design interview question.
</div>

---

# Where This Shortcut Shows Up

<div class="appgrid">
<div class="app"><div class="name">Engineering</div><div class="desc">Testing a bridge or car crash solves the same-shaped system for every test case</div></div>
<div class="app"><div class="name">Weather</div><div class="desc">Forecasts resolve a similar system again, every few minutes, all day long</div></div>
<div class="app"><div class="name">Graphics</div><div class="desc">Games and movies reuse the same setup to move thousands of objects</div></div>
<div class="app"><div class="name">Power grids</div><div class="desc">Operators check grid stability by resolving the same layout, over and over</div></div>
<div class="app"><div class="name">GPS</div><div class="desc">Your phone reuses its setup every second; only the readings change</div></div>
<div class="app"><div class="name">Recommenders</div><div class="desc">Shopping and video apps reuse a solved model as new ratings arrive</div></div>
</div>

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"If a system's left side never changes, can we solve it once and reuse that work forever?"</div>

---

<!-- Key Words for 차시 1 -->

# Key Words Today

<div class="thread">4 words you will hear all week. Learn them now.</div>

- **Factor:** break one grid of numbers into two simpler grids
- **Triangular matrix:** a grid with zeros on one whole side of the diagonal
- **Reuse:** solving a new problem using work already done, not starting over
- **Right-hand side:** the known totals on the equations' right side, called `b`

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

1. Factor a square grid of numbers into two triangular pieces
2. Solve a triangular system quickly, top to bottom or bottom to top
3. Reuse one factoring to solve many systems that share the same left side
4. Explain why factoring once beats solving from scratch every time

---

# Coming Up: Worksheet Part A

Next session, you factor the Café's own recipe grid, by hand.

Then you reuse it to solve two different days, fast.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who first reused a solved grid, and why?</div>

---

<!-- Key Words for 차시 2 -->

# Key Words Today

<div class="thread">5 more words for this session.</div>

- **L (lower triangular):** the grid that stores the elimination multipliers
- **U (upper triangular):** the simplified grid elimination leaves behind
- **Forward substitution:** solving the `L` grid, top to bottom
- **Back substitution:** solving the `U` grid, bottom to top
- **Pivoting:** swapping two rows when the simple method gets stuck

---

<!-- SLOT 8: Origin -->

# Where This Idea Came From

<div class="thread">You just felt this pain. Others felt it too, long before you.</div>

- **1878, USA:** Myrick Doolittle, at the U.S. Coast and Geodetic Survey, factors a grid once to solve many nearly-identical survey problems
- **1948, England:** Alan Turing studies rounding errors in this method, to make it reliable on early digital computers

<div class="why">
Different problem, same shape: many similar systems to solve, one
factoring, reused every time, instead of starting over.
</div>

---

# A Hundred Years of Reuse

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1878</div><div class="d">Doolittle, survey data<br>factor once, reuse often</div></div>
<div class="pt"><div class="dot"></div><div class="y">1948</div><div class="d">Turing, rounding errors<br>method made reliable</div></div>
<div class="pt"><div class="dot"></div><div class="y">1970s</div><div class="d">Numerical software<br>factoring built into every library</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Engineering, graphics, forecasting<br>the same shortcut, everywhere</div></div>
</div>

This method survived because the same problem, solved again and
again, never went away.

---

<!-- SLOT 9: Core concept -->

# LU Factorization: Definition

<div class="thread">Now the exact, formal definition.</div>

> Given a square grid of numbers `A`, an **LU factorization** writes
> `A = LU`. `L` is lower triangular with 1s on its diagonal, and `U`
> is upper triangular.

- `L` stores the multipliers used while simplifying `A`
- `U` is the simplified grid that elimination leaves behind
- Once found, `A = LU` solves `Ax = b` for **any** `b`, using two easy triangular solves

---

<!-- Act 3 / BUILD -->

# Two Kinds of Easy Grids

<div class="thread">Triangular grids are the whole trick. Here is why they are easy.</div>

Two triangular grids, side by side:

```
L = [ 1    0 ]        U = [ 2   1  ]
    [ 0.5  1 ]            [ 0  2.5 ]
```

- `L` has zeros above the diagonal
- `U` has zeros below the diagonal
- Each row of a triangular system has only one new unknown to find

A triangular system needs no more elimination. Read the answer off,
one row at a time.

---

# From Elimination to Two Grids

<div class="thread">You already know how to simplify a grid. LU factoring just saves the steps.</div>

While simplifying `A`, one row is scaled and added to another. That
scaling number is called a **multiplier**.

```
Row 2 = Row 2 − 0.5 × Row 1
```

- Save the multiplier (`0.5`) into `L`
- Save the simplified row into `U`

`A = LU` is a record of elimination, not a new calculation.

---

# Solve Once, Reuse Forever

<div class="thread">This is the whole point of this week.</div>

<div class="pipeline">
<div class="stage"><div class="h">Factor</div><div class="s">A = LU, done once</div></div>
<div class="arrow">→</div>
<div class="stage"><div class="h">Forward</div><div class="s">solve Ly = b</div></div>
<div class="arrow">→</div>
<div class="stage"><div class="h">Back</div><div class="s">solve Ux = y</div></div>
<div class="arrow">→</div>
<div class="stage"><div class="h">Answer</div><div class="s">x, for this b</div></div>
</div>

Only the last two steps repeat for a new `b`. Factoring never
repeats. This split is the entire reason LU factorization exists.

---

# Why Reuse Is Faster: Counting the Work

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">Fresh elimination, every new day</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">full work, every time</div>
</div>
<div class="bar-row">
  <div class="bar-label">Factor once (Monday only)</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 60%"></div></div>
  <div class="bar-value">one-time cost</div>
</div>
<div class="bar-row">
  <div class="bar-label">Reuse for Tuesday, Wednesday, ...</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">two quick solves only</div>
</div>
</div>
<div class="bar-note">illustrative, not measured data</div>

Factoring costs more, once. Every reuse after that costs far less.

---

# Solving a Triangular Grid, Directly

<div class="thread">Before the café's numbers, watch the shortcut work on its own.</div>

A lower triangular system solves top to bottom. Each row adds only
one new unknown:

```
y1 = 6
2(y1) + y2 = 10   →   y2 = -2
```

An upper triangular system solves bottom to top, the same idea in
reverse:

```
3(x2) = -6      →   x2 = -2
x1 + x2 = 4      →   x1 = 6
```

No elimination needed here. Just read each unknown off, one row at a
time.

---

# Demo, Step by Step: Factoring the Café's Recipe (1/5)

<div class="thread">The same Latte and Mocha recipe from Week 1. Let's factor it once.</div>

One unit milk costs `m`. One unit syrup costs `s`. The recipe never
changes:

```
2m + s = (Latte total)
m + 3s = (Mocha total)
```

As a grid of numbers, the left side is:

```
A = [ 2  1 ]
    [ 1  3 ]
```

---

# Demo, Step by Step: Factoring the Café's Recipe (2/5)

**Find the multiplier.** To zero out the `1` in row 2, scale row 1 by
`0.5` and subtract:

```
Row 2 = Row 2 − 0.5 × Row 1
      = [1, 3] − 0.5×[2, 1] = [0, 2.5]
```

Save `0.5` into `L`. The result becomes row 2 of `U`.

---

# Demo, Step by Step: Factoring the Café's Recipe (3/5)

**Write `L` and `U`.**

```
L = [ 1    0 ]        U = [ 2   1  ]
    [ 0.5  1 ]            [ 0  2.5 ]
```

Check: multiplying `L` by `U` rebuilds the original recipe grid `A`.
This factoring is done, once, forever.

---

# Demo, Step by Step: Factoring the Café's Recipe (4/5)

**Monday's receipts:** Latte totaled 800 원, Mocha totaled 900 원.

Forward substitution, solve `Ly = b`:

```
y1 = 800
0.5(800) + y2 = 900   →   y2 = 500
```

Back substitution, solve `Ux = y`:

```
2.5(x2) = 500          →   x2 = 200 (s)
2(x1) + 200 = 800       →   x1 = 300 (m)
```

Monday: `m = 300`, `s = 200`. Matches Week 1's answer, exactly.

---

# Demo, Step by Step: Factoring the Café's Recipe (5/5)

**Tuesday's receipts changed:** Latte totaled 700 원, Mocha totaled
1100 원.

The recipe grid `A` is the same. Reuse `L` and `U`, no re-factoring:

```
y1 = 700
0.5(700) + y2 = 1100   →   y2 = 750
2.5(x2) = 750           →   x2 = 300 (s)
2(x1) + 300 = 700        →   x1 = 200 (m)
```

Tuesday: `m = 200`, `s = 300`. Two quick solves, no fresh elimination.

---

<!-- Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week05/worksheet.html">Worksheet Part A</a>.</div>

Factor the Café's recipe grid yourself, by hand.

Then solve Monday's receipts using forward and back substitution.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to check by multiplying L by U back into A. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: reuse your factoring for two more days.</div>

---

<!-- Key Words for 차시 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Operation count:** how many arithmetic steps a method needs
- **One-time cost:** work done only once, no matter how many times we reuse it
- **Repeat cost:** small work redone every time, only when the right-hand side changes

---

# When the Simple Recipe Isn't Enough

<div class="thread">One nuance before we finish: this shortcut sometimes needs a small fix first.</div>

The Café's recipe grid never needed a row swap. Some grids do.

If elimination would divide by zero, swap two rows first, then
factor. This swap is called **pivoting**.

Pivoting happens before `L` and `U` are built, not after. Once
pivoted, the same forward-and-back-substitution shortcut still works.

---

<!-- SLOT N-2: Worked example -->

# Case Study: A Third Day, Same Recipe

<div class="thread">The running Café example, one more time, reused.</div>

Wednesday's receipts: Latte totaled 900 원, Mocha totaled 1200 원. No
new elimination needed. Reuse the same `L` and `U` from before:

```
y1 = 900
0.5(900) + y2 = 1200   →   y2 = 750
2.5(x2) = 750            →   x2 = 300 (s)
2(x1) + 300 = 900         →   x1 = 300 (m)
```

Wednesday: `m = 300`, `s = 300`. Three days, one factoring, three
fast solves.

---

<!-- Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week05/worksheet.html">Worksheet Part B</a>.</div>

Reuse your Part A factoring for two brand-new days' receipts.

Then answer: why didn't you redo elimination?

You have about 15 minutes.

---

# Common Mistakes

- **Re-factoring every time:** once `L` and `U` are found, never redo elimination for a new `b`
- **Solving out of order:** always solve `Ly = b` first, then `Ux = y`, never the reverse
- **Skipping the pivot check:** some grids need one row swap first, or the simple method breaks

---

# Check Yourself

1. True or false: once you know `L` and `U`, you can reuse them for any new right-hand side.
2. A third day arrives with new receipts. What two steps solve it?
3. Thursday's receipts: Latte totaled 1000 원, Mocha totaled 1500 원. Find `m` and `s`.

---

# Answers

1. **True.** `L` and `U` depend only on the recipe grid, never on the day's receipts.
2. **Forward substitution** (`Ly = b`), then **back substitution** (`Ux = y`).
3. `m = 300`, `s = 400`. (`y1 = 1000`, `y2 = 1500 − 500 = 1000`, `x2 = 400`, `x1 = (1000 − 400)/2 = 300`.)

---

<!-- Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week05/quiz.html">Week 5 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 6 slot 4 -->

# What LU Factorization Cannot Do

<div class="limits">
LU factorization makes solving fast, once we already know the recipe
grid. But it never tells us which totals a recipe can even reach.
Some combinations of milk and syrup cost are simply impossible for a
fixed recipe to produce. LU factorization speeds up solving, but
tells us nothing about which directions in space a system actually
reaches.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 5 leaves one thing unsolved: **which directions in space a
system actually reaches.** **Week 6, Determinants**, addresses part
of this: a single number that tells us whether a solution exists,
and is unique.

---

<!-- SLOT 16: Summary -->

# Summary

- LU factorization writes a grid `A` as `L` times `U`, two triangular pieces
- Factor once; then forward and back substitution solve any new right-hand side, fast
- Reuse beats restarting, in the Café, in engineering, and in every large simulation
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 2.5
- **Handout:** [materials/week05/handout.md](materials/week05/handout.html), glossary and the full three-day walkthrough
- **Prepare:** think of one place in your own life where you redo the same work, instead of reusing it

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
