---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 12: Orthogonality

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "Can two lists of numbers point the same way?" Today
answers that exactly.
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
<div class="wk now"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: we now measure vectors, not just transform them. -->

---

<!-- SLOT 3: Recap + open wound -->

# Last Week, This Week

- **Last week delivered:** diagonalization makes repeated transformations fast
- **Last week left broken:** it only measures stretching, not angle or distance

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# Two Recipes, One Confusing Question

<div class="pain">

The Campus Café now sells many drinks. Two new drinks share the same
two ingredients, milk and syrup, in different amounts.

A regular customer asks: "Do these two drinks basically taste the
same, just bigger, or are they truly different?"

Staff cannot answer just by looking at the numbers. They cannot say
how far apart the two recipes are, or whether they lean toward the
same flavor.

All they can do is guess, mix both, and taste-test again.

</div>

<!-- notes: Do not say "vector," "angle," or "length" as math terms yet.
Let the guessing feel uncomfortable first. -->

---

# More Drinks, More Guesswork

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">2 drinks on the menu</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 10%"></div></div>
  <div class="bar-value">1 pair to compare</div>
</div>
<div class="bar-row">
  <div class="bar-label">5 drinks on the menu</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 45%"></div></div>
  <div class="bar-value">10 pairs to compare</div>
</div>
<div class="bar-row">
  <div class="bar-label">10 drinks on the menu</div>
  <div class="bar-track"><div class="bar-fill risk-high" style="width: 100%"></div></div>
  <div class="bar-value">45 pairs to compare</div>
</div>
</div>
<div class="bar-note">every new drink adds a comparison against every drink already on the menu</div>

Taste-testing every pair does not scale. This week finds an exact way
to compare any two recipes, without tasting either one.

<!-- notes: Let the widening bars sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Taste-testing near-duplicate drinks wastes ingredients and staff time
- A confusing menu, full of drinks nobody can tell apart, loses sales
- A data scientist who cannot measure "how similar" two items are cannot build a working recommendation feature

<div class="why">
<strong>In industry:</strong> measuring the angle between two lists of
numbers, not just their size, is the exact idea behind recommendation
engines, search ranking, and face matching. It is a common question in
data science interviews.
</div>

---

# Same Idea, Many Fields

<div class="appgrid">
<div class="app"><div class="name">Recommendation engines</div><div class="desc">Compares taste vectors by angle, not just by total amount</div></div>
<div class="app"><div class="name">GPS and robotics</div><div class="desc">Computes the exact distance between two positions</div></div>
<div class="app"><div class="name">Face and image search</div><div class="desc">Compares feature vectors to find the closest match</div></div>
</div>

<!-- notes: One line: same shape as the café problem, bigger stakes. -->

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we measure the exact length of a vector, and the exact angle between two vectors?"</div>

---

<!-- NEW: Key Words for 차시 1 -->

# Key Words Today

<div class="thread">4 words you will hear all class. Learn them now.</div>

- **Dot product:** multiply matching numbers from two vectors, then add every result together
- **Length (norm):** how long a vector is, found from its dot product with itself
- **Distance:** how far apart two vectors are
- **Orthogonal:** two vectors that meet at a right angle; their dot product is zero

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

1. Compute the dot product and length of a vector
2. Compute the exact angle between two vectors
3. Test whether two vectors are orthogonal
4. Build a unit vector and recognize an orthogonal set

---

<!-- NEW: preview hook, ends 차시 1 -->

# Coming Up: Worksheet Part A

Next session, you compute the exact length and distance for real
café recipes.

You also learn where this way of measuring vectors came from.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who first measured length and angle this way, and why?</div>

---

<!-- NEW: Key Words for 차시 2 -->

# Key Words Today

<div class="thread">3 more words for this session.</div>

- **Angle:** how far apart two vectors point, measured in degrees
- **Cosine:** a formula that turns a dot product and two lengths into an angle
- **Magnitude:** another name for a vector's length

---

<!-- SLOT 8: Origin -->

# This Way of Measuring Is Not New

<div class="thread">You just felt this pain. Others felt it too, long before you.</div>

- **~300 BCE, Greece:** Euclid's *Elements* proves the Pythagorean theorem, the first exact way to find a length from perpendicular parts
- **1880s, USA:** Josiah Willard Gibbs and Oliver Heaviside write the modern dot product, for force and work in physics

<div class="why">
The same formula that once measured force in physics now measures
how similar two customers' tastes are.
</div>

---

# From Right Triangles to Recommendation Engines

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">~300 BCE</div><div class="d">Euclid<br>length from right angles</div></div>
<div class="pt"><div class="dot"></div><div class="y">1844</div><div class="d">Grassmann<br>length and angle, beyond 3 dimensions</div></div>
<div class="pt"><div class="dot"></div><div class="y">1880s</div><div class="d">Gibbs &amp; Heaviside<br>the modern dot product, for physics</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Search &amp; recommendation<br>the same angle formula, at massive scale</div></div>
</div>

This formula survived 2,000 years because measuring length and angle
never stopped mattering.

---

<!-- SLOT 9: Core concept -->

# Dot Product & Length: Definition

<div class="thread">Now the exact, formal definition.</div>

> The **dot product** of two vectors u = (u₁, u₂, ..., uₙ) and
> v = (v₁, v₂, ..., vₙ) is one number:
>
> ```
> u · v = u₁v₁ + u₂v₂ + ... + uₙvₙ
> ```
>
> The **length**, or **norm**, of a vector u is
>
> ```
> ||u|| = √(u · u)
> ```

- The dot product turns two vectors into a single number
- A vector's length is never negative, and is zero only for the zero vector

---

<!-- Act 3 / BUILD -->

# Computing the Dot Product

<div class="thread">One rule: multiply matching positions, then add.</div>

For u = (1, 2) and v = (3, 4), multiply matching entries, then add
the results:

```
u · v = (1)(3) + (2)(4) = 3 + 8 = 11
```

The same rule works for any number of entries: multiply each matching
pair, then add every result together.

---

# Properties of the Dot Product

<div class="thread">Two rules make the dot product easy to reuse.</div>

The dot product does not care about order:

```
u · v = v · u
```

It also spreads across addition, the same way multiplication does:

```
u · (v + w) = u · v + u · w
```

These two rules let you simplify a dot product before computing it,
the same way you would with ordinary numbers.

---

# Length of a Vector (the Norm)

<div class="thread">Length is the dot product of a vector with itself, then a square root.</div>

For u = (3, 4):

```
||u|| = √(u · u) = √(3² + 4²) = √(9 + 16) = √25 = 5
```

This is the Pythagorean theorem, applied to a vector instead of a
triangle. The same formula works in any number of dimensions.

---

# Distance Between Two Vectors

<div class="thread">Distance reuses length: it is the length of the difference.</div>

For u = (1, 2) and v = (4, 6), first subtract, then find the length:

```
u - v = (1 - 4, 2 - 6) = (-3, -4)
||u - v|| = √((-3)² + (-4)²) = √25 = 5
```

The **distance** between two vectors is the length of one minus the
other, no matter how many entries they have.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week12/worksheet.html">Worksheet Part A</a>.</div>

Compute the dot product, length, and distance for two real café
recipes.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. Remind them length always uses
a square root; the dot product alone gives length squared. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: turn length and distance into an exact angle.</div>

---

<!-- NEW: Key Words for 차시 3 -->

# Key Words Today

<div class="thread">4 words for the last part of this week.</div>

- **Unit vector:** a vector with length exactly 1
- **Normalize:** shrink or stretch a vector to length 1, without changing its direction
- **Orthogonal set:** a group of vectors that are all orthogonal to each other, every pair
- **Orthonormal set:** an orthogonal set where every vector is also a unit vector

---

# The Angle Between Two Vectors

<div class="thread">The dot product and both lengths together give the exact angle.</div>

```
cos(angle) = (u · v) / (||u|| · ||v||)
```

For u = (3, 4) and v = (4, 3):

```
u · v = 12 + 12 = 24
||u|| = 5, ||v|| = 5
cos(angle) = 24 / 25 = 0.96
```

A calculator's inverse-cosine button turns 0.96 into about 16°: these
two vectors point in nearly the same direction.

---

# Reading the Angle

<div class="thread">A few landmark values are worth memorizing.</div>

| cos(angle) | Angle | Meaning |
|---|---|---|
| 1 | 0° | Same direction exactly |
| 0.5 | 60° | Somewhat similar |
| 0 | 90° | Orthogonal, no shared direction |
| -1 | 180° | Exactly opposite directions |

A cosine near 1 means "very similar." A cosine near 0 means "barely
related." This is exactly how recommendation engines rank matches.

---

# Orthogonal Vectors

<div class="thread">One special angle needs no calculator at all: exactly 90°.</div>

Two vectors are **orthogonal** exactly when their dot product is
zero. For u = (3, 4) and v = (4, -3):

```
u · v = (3)(4) + (4)(-3) = 12 - 12 = 0
```

The dot product is zero, so u and v meet at a right angle. This test
works in any number of dimensions, even where you cannot draw a
picture.

---

# The Zero Vector Is Orthogonal to Everything

<div class="thread">One edge case surprises most students the first time.</div>

The all-zero vector, `0 = (0, 0, ..., 0)`, has a dot product of zero
with every other vector:

```
u · 0 = u₁(0) + u₂(0) + ... + uₙ(0) = 0
```

So the zero vector counts as orthogonal to every vector, including
itself. It has no direction to disagree with.

---

# Unit Vectors and Normalizing

<div class="thread">Comparing pure direction means removing size first.</div>

To **normalize** a vector, divide it by its own length. For
u = (3, 4), with length 5:

```
unit vector = (3/5, 4/5) = (0.6, 0.8)
```

The result always has length 1. Normalizing keeps the direction, and
throws away only the size.

---

# Orthogonal Sets

<div class="thread">The two ideas combine: orthogonal, and length 1, at once.</div>

Vectors (3, 4) and (4, -3) are orthogonal. Normalize both:

```
(0.6, 0.8)  and  (0.8, -0.6)
```

Check: `(0.6)(0.8) + (0.8)(-0.6) = 0.48 - 0.48 = 0`. Still orthogonal,
and both now have length 1. This is an **orthonormal set**.

---

# Why Orthogonal Sets Make Life Easier

<div class="thread">One reason this idea matters beyond today.</div>

Directions that never overlap are easy to combine and easy to
separate. An orthogonal set is automatically independent: no vector
in it can be built from the others.

Later courses build coordinate systems and computer graphics almost
entirely out of orthonormal sets, because the arithmetic stays this
simple.

---

# Length, Distance, and Angle: What Each One Answers

<div class="thread">Three tools, three different questions.</div>

| Tool | Question it answers |
|---|---|
| Length | How big is one vector, by itself? |
| Distance | How far apart are two vectors' raw amounts? |
| Angle | How similar are two vectors' directions, ignoring size? |

Two recipes can sit far apart in raw amounts, yet still point in
nearly the same direction. Angle and distance measure different
things.

---

<!-- SLOT N-2: Worked example -->

# Case Study: Comparing Two Café Recipes (1/2)

<div class="thread">Back to the pain: are these two drinks basically the same, or not?</div>

Recall Week 1's two drinks, written as (milk, syrup) vectors:

```
Latte = (2, 1)      Mocha = (1, 3)
```

```
Latte · Mocha = (2)(1) + (1)(3) = 2 + 3 = 5
||Latte|| = √(4 + 1) = √5
||Mocha|| = √(1 + 9) = √10
```

---

# Case Study: Comparing Two Café Recipes (2/2)

Put the dot product and both lengths into the angle formula:

```
cos(angle) = 5 / (√5 · √10) = 5 / √50 = 1 / √2 ≈ 0.707
angle ≈ 45°
```

The Latte and Mocha lean 45° apart: partly similar, partly different,
neither identical nor opposite. Now staff have an exact number, not a
guess.

<!-- notes: This is the payoff of the pain slide: an exact, repeatable
answer to "how similar are these two drinks," with no extra tasting. -->

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week12/worksheet.html">Worksheet Part B</a>.</div>

Compute the angle between two more recipes. Then classify three
vector pairs as orthogonal or not.

You have about 15 minutes.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

- **Skipping the square root:** the dot product of a vector with itself gives length squared, not length
- **Assuming a negative dot product means "opposite":** it only means the angle is greater than 90°, not exactly 180°
- **Judging orthogonality by eye:** in three or more dimensions you cannot see a right angle. Always check the dot product instead
- **Forgetting to normalize both vectors:** an orthonormal set needs every vector at length 1, not just some of them

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Find the length of u = (6, 8).
2. Are v = (1, 2) and w = (2, -1) orthogonal? Show the dot product.
3. Normalize u = (0, 5) into a unit vector.

---

# Answers

1. `||u|| = √(36 + 64) = √100 = 10`.
2. `v · w = (1)(2) + (2)(-1) = 2 - 2 = 0`. **Yes, orthogonal.**
3. Length of u is `5`, so the unit vector is `(0/5, 5/5) = (0, 1)`.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week12/quiz.html">Week 12 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT N+1: Limits (Act 4 / CLOSE), becomes Week 13 slot 4 -->

# What This Week's Method Cannot Do Yet

<div class="limits">
We can measure angle and length exactly, and test whether two vectors
are orthogonal. But we still cannot find the closest point in a whole
subspace to a point that sits outside it. Knowing two things are 45°
apart does not yet tell us the nearest match inside a larger space of
options.
</div>

---

<!-- SLOT N+2: Bridge -->

# Next Week

Week 12 leaves one thing unsolved: **finding the closest point in a
subspace to a point outside it.** **Week 13, Projections**, addresses
it, building directly on this week's length and angle.

---

<!-- SLOT N+3: Summary -->

# Summary

- The dot product turns two vectors into one number; length is the square root of a vector dotted with itself
- The angle formula, `cos(angle) = (u · v) / (||u|| · ||v||)`, measures how similar two vectors' directions are
- Two vectors are orthogonal exactly when their dot product is zero; normalizing gives a unit vector for pure direction
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 6
- **Handout:** [materials/week12/handout.md](materials/week12/handout.html), glossary and the full café walkthrough
- **Prepare:** think of one time you needed the *closest* match, not just a similarity score. Bring it to Week 13

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
