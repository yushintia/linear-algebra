---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 13: Projections

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "Have you ever tried to match something exactly, and only
got close?" That feeling is today's hook.
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
<div class="wk"><div class="n">Wk 6</div><div class="t">Determinants</div></div>
<div class="wk"><div class="n">Wk 7</div><div class="t">Vector Spaces · Quiz 1</div></div>
<div class="wk review"><div class="n">Wk 8</div><div class="t">Midterm Exam</div></div>
<div class="wk"><div class="n">Wk 9</div><div class="t">Bases, Dimension</div></div>
<div class="wk"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk now"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: we now find the closest point, not just measure angle and length. -->

---

<!-- SLOT 3: Recap + open wound -->

# Last Week, This Week

- **Last week delivered:** we can measure angle and length between two recipe vectors, and check whether two are orthogonal
- **Last week left broken:** we can measure angle and length, but not yet find the closest point in a subspace to a point outside it

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# A Drink the New Machine Can't Make

<div class="pain">

The Campus Café bought a new blending machine. It only mixes drinks
from two fixed starter mixes, Mix P and Mix Q, in any amount.

A regular customer orders their usual drink: a specific blend of
espresso, milk, and syrup that always tasted right before.

The machine cannot make that exact blend. The two starter mixes only
reach some possible drinks, not every drink.

The barista needs the closest drink the machine can actually make.
Guessing amounts by feel still wastes syrup and time.

</div>

<!-- notes: Do not say "vector," "orthogonal," or "projection" yet.
Let the mismatch sit uncomfortably before naming anything. -->

---

# Guessing the Closest Match Gets Harder

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">One shared ingredient axis</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 20%"></div></div>
  <div class="bar-value">guessing is close enough</div>
</div>
<div class="bar-row">
  <div class="bar-label">Two starter mixes, 3 ingredients</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 60%"></div></div>
  <div class="bar-value">guessing rarely lands close</div>
</div>
<div class="bar-row">
  <div class="bar-label">A full menu, many ingredients</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">guessing almost never matches</div>
</div>
</div>

Guessing does not scale to more ingredients. This week computes the
closest match exactly.

<!-- notes: Let the widening bars sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Wasted syrup and time, whenever the barista guesses instead of computing the closest match
- A robot arm that cannot find the closest reachable position may miss its target or collide
- A photo or audio app that cannot find the closest clean signal keeps the noise in

<div class="why">
<strong>In industry:</strong> finding the closest achievable point sits
behind robotics motion planning, computer graphics reflections, and
noise removal. It is also the geometric idea behind least-squares
fitting, a common data-science interview topic.
</div>

---

# Same Idea, Many Fields

<div class="appgrid">
<div class="app"><div class="name">Robotics</div><div class="desc">Finds the closest reachable arm position to a target point</div></div>
<div class="app"><div class="name">Computer graphics</div><div class="desc">Draws a shadow or mirror reflection as a projection onto a surface</div></div>
<div class="app"><div class="name">Signal processing</div><div class="desc">Keeps the closest clean signal, dropping whatever does not fit the pattern</div></div>
</div>

<!-- notes: One line: same shape as the café problem, bigger stakes. -->

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we find the closest point in a subspace to a point outside it?"</div>

---

<!-- NEW: Key Words for 차시 1 -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Projection:** the closest point in a line or subspace to a given point
- **Line through the origin:** a straight line that passes through the zero point
- **Distance:** how far apart two points are, measured in a straight line
- **Residual (leftover):** the part of a point that a subspace cannot reach
- **Closest point:** the one point in a subspace nearest to a given point

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

1. Project a vector onto a line through the origin
2. Project a vector onto a subspace using an orthogonal basis
3. Split a vector into an in-subspace part and a leftover part
4. Explain why the projection is the closest point in the subspace

---

<!-- NEW: preview hook, ends 차시 1 -->

# Coming Up: Worksheet Part A

Next session, you find the closest point on a line, by hand.

Then you check your answer using the projection formula.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who first computed the closest match, and why?</div>

---

<!-- NEW: Key Words for 차시 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Orthogonal basis:** a set of basis vectors that are all at right angles to each other
- **Achievable set:** every point a subspace can reach, like every drink the machine can mix
- **Orthogonal decomposition:** splitting a vector into an in-subspace part plus a leftover part
- **Best approximation:** the closest possible match, whenever an exact match is not available

---

<!-- SLOT 8: Origin -->

# The Closest Match Is an Old Problem

<div class="thread">You just felt this pain. Astronomers felt it two centuries ago.</div>

- **1805, France:** Adrien-Marie Legendre publishes a method to find the closest-fitting orbit through scattered observations
- **1809, Germany:** Carl Friedrich Gauss, the same mathematician from Week 1's story, claims he used the same idea even earlier
- **1907, Germany:** Erhard Schmidt formalizes how to build an orthogonal basis, making the projection formula simple to use

<div class="why">
Different problem, same shape: an exact answer does not exist, so
find the nearest one instead.
</div>

---

# From Scattered Stars to Every Field

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1805</div><div class="d">Legendre<br>closest-fitting orbit, first published</div></div>
<div class="pt"><div class="dot"></div><div class="y">1809</div><div class="d">Gauss<br>claims the same idea, earlier</div></div>
<div class="pt"><div class="dot"></div><div class="y">1907</div><div class="d">Schmidt<br>orthogonal basis, formalized</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Robotics, graphics, data science<br>the same method, everywhere</div></div>
</div>

One idea, over 200 years old, still finds the closest match today.

---

<!-- SLOT 9: Core concept -->

# Projection Onto a Line: Definition

<div class="thread">Now the exact, formal definition.</div>

> Let `u` be a nonzero vector. The **projection** of a vector `y` onto
> the line through the origin spanned by `u` is
>
> ```
> proj_u(y) = ((y · u) / (u · u)) u
> ```
>
> This is the one point on that line closest to `y`.

- `y · u` is the **dot product**: multiply matching entries, then add them
- `u · u` is `u`'s squared length; dividing by it never changes `u`'s direction

---

<!-- Act 3 / BUILD -->

# A Small Example First

<div class="thread">Before the café, try the formula on plain numbers.</div>

Project `y = (4, 1)` onto the line spanned by `u = (1, 1)`.

```
y · u = 4(1) + 1(1) = 5
u · u = 1(1) + 1(1) = 2
proj_u(y) = (5 / 2)(1, 1) = (2.5, 2.5)
```

The closest point on that line to `(4, 1)` is `(2.5, 2.5)`.

---

# Why This Point Is the Closest

<div class="thread">The formula is not a guess. A right angle proves it.</div>

The leftover part `z = y - proj_u(y)` always forms a right angle with
`u`:

```
z = (4, 1) - (2.5, 2.5) = (1.5, -1.5)
z · u = 1.5(1) + (-1.5)(1) = 0
```

A right angle marks the shortest path from `y` to the line. Every
other point on the line sits farther away.

---

# Checking a Projection Two Ways

<div class="thread">Two independent checks catch almost every mistake.</div>

**Check 1, right angle:** compute `z · u`. It must equal 0.

**Check 2, distance:** the projection should sit nearer to `y` than
any other point on the line.

```
Try (1, 1) instead of (2.5, 2.5):
distance from y to (1, 1)     = 3.00
distance from y to proj_u(y)  = 2.12
```

The projection wins both checks. Any other point on the line loses at
least one.

---

# From a Point to Its Closest Match

<div class="pipeline">
<div class="stage"><div class="h">1. Pick</div><div class="s">Choose the line or subspace to project onto</div></div>
<div class="arrow">&rarr;</div>
<div class="stage"><div class="h">2. Compute</div><div class="s">Apply the projection formula to `y`</div></div>
<div class="arrow">&rarr;</div>
<div class="stage"><div class="h">3. Read off</div><div class="s">The result is the closest point, guaranteed</div></div>
</div>

These three steps never change, no matter how many ingredients or
unknowns the problem has.

---

# Projecting Onto a Subspace With Two Directions

<div class="thread">A subspace can be bigger than one line. The formula still works, one direction at a time.</div>

If `u1` and `u2` are **orthogonal** (`u1 · u2 = 0`), the projection
onto their span adds each line's projection:

```
proj_W(y) = ((y·u1)/(u1·u1)) u1 + ((y·u2)/(u2·u2)) u2
```

This only works when `u1` and `u2` are orthogonal. Non-orthogonal
directions need a different method, not covered this week.

---

# Why Orthogonal Directions Matter

<div class="thread">Last week's skill is not optional here. It is required.</div>

If `u1` and `u2` point in unrelated directions (`u1 · u2 = 0`), each
direction's share of `y` never overlaps with the other.

If `u1` and `u2` were not orthogonal, adding their two projections
would double-count part of `y`, and the simple formula would give the
wrong point.

This is why last week's orthogonality check always comes first.

---

# Splitting a Vector in Two

<div class="thread">Every projection also produces a leftover. Together, they rebuild the original vector.</div>

<div class="stack">
<div class="layer view"><div class="h">ŷ — the achievable part</div><div class="s">Inside the subspace; the closest match</div></div>
<div class="layer logical"><div class="h">z — the leftover part</div><div class="s">Orthogonal to the subspace; what could not fit</div></div>
</div>

```
y = ŷ + z
```

This is the **orthogonal decomposition**: any vector splits into an
in-subspace part and a leftover part, at a right angle to it.

---

# The Café's Machine, Pictured

<div class="appgrid">
<div class="app"><div class="name">Mix P alone</div><div class="desc">Reaches every point on one line: equal espresso and milk, no syrup</div></div>
<div class="app"><div class="name">Mix Q alone</div><div class="desc">Reaches every point on another line: pure syrup, no espresso or milk</div></div>
<div class="app"><div class="name">P and Q together</div><div class="desc">Reaches every point on the flat plane through both lines</div></div>
</div>

The customer's drink sits off that plane. The projection finds the
nearest point still on it.

---

<!-- SLOT N-2: Worked example -->

# Case Study: The Café's Two Starter Mixes (1/3)

<div class="thread">Back to the pain: a drink the new machine cannot make exactly.</div>

Mix P uses equal espresso and milk. Mix Q is pure syrup, in
(espresso, milk, syrup) order:

```
P = (1, 1, 0)
Q = (0, 0, 1)
```

Last week's method already confirmed `P · Q = 0`: the two mixes are
orthogonal. The machine only makes drinks of the form `aP + bQ`, for
any amounts `a` and `b`.

---

# Case Study: The Café's Two Starter Mixes (2/3)

The customer's usual drink is `y = (3, 1, 4)`, in (espresso, milk,
syrup). It is not reachable: `aP + bQ = (a, a, b)` always needs equal
espresso and milk, but `y` does not.

Compute the projection:

```
(y·P)/(P·P) = (3+1+0)/(1+1+0) = 4/2 = 2
(y·Q)/(Q·Q) = (0+0+4)/(0+0+1) = 4/1 = 4
proj_W(y) = 2P + 4Q = (2, 2, 0) + (0, 0, 4) = (2, 2, 4)
```

The closest drink the machine can make is `(2, 2, 4)`.

---

# Case Study: The Café's Two Starter Mixes (3/3)

The leftover part:

```
z = y - proj_W(y) = (3, 1, 4) - (2, 2, 4) = (1, -1, 0)
```

`z` is orthogonal to both `P` and `Q`: check `z·P = 0` and `z·Q = 0`.

`z` shows exactly what does not fit: one extra espresso, one missing
milk. The barista serves `(2, 2, 4)` and knows exactly what changed.

<!-- notes: Point out this directly answers the pain slide: the
barista now has the provably closest drink, not a guess. -->

---

# Where Else the Leftover Matters

- A leftover of zero means the point was already achievable; no approximation was needed
- A large leftover warns that the subspace is a poor match for this point
- Next week, the leftover becomes the **error** in a best-fit line through real data

<div class="why">
Keeping the leftover, not just the closest point, is what makes this
method useful for judging how good a fit really is.
</div>

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week13/worksheet.html">Worksheet Part A</a>.</div>

Project one vector onto a line, by hand.

Then check your answer using the right-angle rule.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask
them to verify the right angle by computing the dot product. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: check your Worksheet A answer, then go further.</div>

---

<!-- NEW: Key Words for 차시 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Minimum distance:** the shortest possible gap between a point and every point in a subspace
- **Error:** another name for the leftover part; how far the closest match still is
- **Best approximation theorem:** the rule stating the projection is always the closest point, no exceptions

---

# The Best Approximation Theorem

<div class="thread">One sentence sums up everything this week has shown.</div>

> For any point `y` and subspace `W`, the projection `ŷ = proj_W(y)`
> is closer to `y` than every other point in `W`:
>
> ```
> ||y - ŷ|| < ||y - v||    for every other point v in W
> ```

No guessing needed. The formula always finds this one best point.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week13/worksheet.html">Worksheet Part B</a>.</div>

Project the café's next order onto two orthogonal starter mixes.

Then find the leftover part and check that it is orthogonal.

You have about 15 minutes.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

- **Adding projections without checking orthogonality:** the two-direction formula only works when `u1 · u2 = 0`; check this first
- **Dividing by the wrong length:** always divide by `u · u`, the squared length, never by `u` alone
- **Expecting the leftover to be zero:** a zero leftover only happens when `y` was already inside the subspace

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Project `y = (3, 4)` onto the line spanned by `u = (2, 0)`.
2. True or false: the leftover vector `z` always forms a right angle with the subspace.

---

# Answers

1. `proj_u(y) = ((6+0)/(4+0))(2, 0) = 1.5(2, 0) = (3, 0)`.
2. **True.** That right angle is exactly what makes the projection the closest point.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week13/quiz.html">Week 13 quiz</a>. Answer alone, no notes.</div>

6 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 14 slot 4 -->

# What Projection Cannot Do Yet

<div class="limits">
Projection finds the closest point in theory, using clean, exact
numbers like the café's starter mixes. But real data rarely has an
exact solution to project onto. A whole survey of noisy customer
answers will not line up as neatly as `P` and `Q` did today. We have
the closest-point idea. We do not yet have a way to apply it to many
messy, real measurements at once.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 13 leaves one thing unsolved: **applying the closest-point idea
to real, noisy data, not just clean vectors.** **Week 14, Least
Squares**, addresses this. It uses real customer taste-test scores,
which never line up exactly, to fit the best approximate recipe.

---

<!-- SLOT 16: Summary -->

# Summary

- Projecting `y` onto a line spanned by `u` gives the one closest point: `proj_u(y) = ((y·u)/(u·u)) u`
- With an orthogonal basis, projecting onto a subspace adds each line's projection together
- Every vector splits into an in-subspace part plus a leftover part, at a right angle to it
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 6, §6.2-6.3
- **Handout:** [materials/week13/handout.md](materials/week13/handout.html), glossary and the full café walkthrough
- **Prepare:** bring one example of a guess that almost, but not quite, matched reality; Week 14 uses real, noisy customer taste-test data

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
