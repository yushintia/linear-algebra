---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 7: Vector Spaces · Quiz 1

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Remind students Quiz 1 happens near the end of today's third
session. It is short and covers Weeks 1-7.
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
<div class="wk now"><div class="n">Wk 7</div><div class="t">Vector Spaces · Quiz 1</div></div>
<div class="wk review"><div class="n">Wk 8</div><div class="t">Midterm Exam</div></div>
<div class="wk"><div class="n">Wk 9</div><div class="t">Bases, Dimension</div></div>
<div class="wk"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: we now describe whole spaces, not single answers. -->

---

<!-- SLOT 3: Recap + open wound -->

# Last Week, This Week

- **Last week delivered:** a determinant tells us if a solution is unique
- **Last week left broken:** it does not tell us what the whole space of solutions looks like

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# Too Many Right Recipes

<div class="pain">

The Campus Café wants a cheaper version of its drink. Several
ingredient combinations pass every taste rule, not just one.

Staff test one combination, then another, then another. Each new
combination costs another batch, another taste test, another
half-hour.

Nobody can tell the owner what all the working combinations look
like. They can only report the ones they happened to try.

The owner asks: "Just tell me every recipe that works." Nobody on
staff can answer that question.

</div>

<!-- notes: Do not say "vector" or "space" yet. Let the open-ended
frustration sit before naming anything. -->

---

# Every Trial Finds One More, Never All

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">Combinations tried by hand</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 20%"></div></div>
  <div class="bar-value">3 found so far</div>
</div>
<div class="bar-row">
  <div class="bar-label">Combinations that actually work</div>
  <div class="bar-track"><div class="bar-fill risk-high" style="width: 100%"></div></div>
  <div class="bar-value">unknown, maybe endless</div>
</div>
</div>

Trying combinations one at a time never finds them all. This week
finds a way to describe every one at once.

<!-- notes: Let the mismatched bar lengths sit for a second. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Retesting wastes ingredients and staff time, every single week
- An engineer who cannot describe a whole solution space may miss the cheapest safe design
- A data scientist who cannot describe a whole solution space cannot quickly check new data against it

<div class="why">
<strong>In industry:</strong> describing "the space of all valid
options" sits behind circuit design, image compression, and
error-correcting codes. Interviewers often ask candidates to describe
a whole solution space, not just find one answer.
</div>

---

# Same Idea, Many Fields

<div class="appgrid">
<div class="app"><div class="name">Image compression</div><div class="desc">Stores a photo using a small set of building-block directions, not every pixel</div></div>
<div class="app"><div class="name">Error-correcting codes</div><div class="desc">Finds every valid message pattern a phone or disk drive can send</div></div>
<div class="app"><div class="name">Circuit design</div><div class="desc">Describes every current pattern a circuit's rules allow, not just one</div></div>
</div>

<!-- notes: One line: same shape as the café problem, bigger stakes. -->

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we describe an entire solution space, not just one solution?"</div>

---

<!-- NEW: Key Words for 차시 1 -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Vector:** a list of numbers, like a point or a direction
- **Scalar:** a single plain number, used to stretch or shrink a vector
- **Vector space:** a collection of vectors you can add and scale, and always stay inside
- **Subspace:** a smaller vector space that sits inside a bigger one
- **Closure:** staying inside the collection after adding or scaling

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

1. Check whether a set of objects forms a vector space
2. Test whether a subset is a subspace
3. Find the span of a small set of vectors
4. Describe the whole solution set of `Ax = 0` as a subspace

---

<!-- NEW: preview hook, ends 차시 1 -->

# Coming Up: Worksheet Part A

Next session, you check whether real object collections follow the
vector space rules.

You also describe a small solution space directly, in pairs.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who first described spaces this way, and why?</div>

---

<!-- NEW: Key Words for 차시 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Linear combination:** a sum of scaled vectors, like `2v + 3w`
- **Span:** every vector reachable by linear combinations of a set
- **Null space:** every solution to `Ax = 0`, gathered into one set
- **Column space:** every output `Ax` can reach, as `x` varies

---

<!-- SLOT 8: Origin -->

# This Abstraction Is Not New

<div class="thread">Different objects, same rules. Mathematicians noticed this over 150 years ago.</div>

- **1844, Germany:** Hermann Grassmann describes "extended quantities" with more than 3 dimensions, adding and scaling them by rule
- **1888, Italy:** Giuseppe Peano writes down the exact rule list we still use today

<div class="why">
Arrows, matrices, and even functions all obey the same addition and
scaling rules. One rule list describes all of them at once.
</div>

---

# From Arrows to Abstract Spaces

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1844</div><div class="d">Grassmann<br>extended quantities, many dimensions</div></div>
<div class="pt"><div class="dot"></div><div class="y">1888</div><div class="d">Peano<br>the modern rule list, named</div></div>
<div class="pt"><div class="dot"></div><div class="y">1900s</div><div class="d">Hilbert, Banach<br>functions treated as vectors too</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Machine learning<br>data features live in a vector space</div></div>
</div>

One rule list, written in 1888, still describes every space we use
today.

---

<!-- SLOT 9: Core concept -->

# Vector Space: Definition

<div class="thread">Now the exact, formal definition.</div>

> A **vector space** is a set `V`, with addition and scalar
> multiplication, where adding any two elements of `V`, or scaling any
> element of `V`, always gives another element of `V`.
>
> Eight more rules make the arithmetic behave the way you expect: a
> zero element exists, every element has an opposite, and order or
> grouping never changes the result.

- Together, every rule means: you can never add or scale your way out of `V`

---

<!-- Act 3 / BUILD -->

# The Vector Space Rules, Grouped

<div class="thread">Ten rules total. Three ideas cover all of them.</div>

| Group | What it means |
|---|---|
| Closure | Add two elements, or scale one; you never leave the set |
| Identity & opposites | A zero element exists; every element has an opposite that cancels it |
| Familiar arithmetic | Order, grouping, and distributing work the way normal numbers do |

Most sets fail on closure first. Check that rule first, always.

---

# Not Every Set Is a Vector Space

<div class="thread">One broken rule is enough to disqualify a set.</div>

| Set | Vector space? | Why |
|---|---|---|
| All pairs `(x, y)` of real numbers | Yes | Adding or scaling any pair gives another pair |
| All pairs `(x, y)` with `x ≥ 0` | No | Scaling `(1, 0)` by `-1` leaves the set |
| All 2×2 matrices | Yes | Adding or scaling any matrix gives another 2×2 matrix |
| Points on a line not through zero | No | No zero element sits on that line |

---

# Real Vector Spaces You Already Use

<div class="appgrid">
<div class="app"><div class="name">Rⁿ</div><div class="desc">Lists of n numbers, like ingredient amounts</div></div>
<div class="app"><div class="name">m×n matrices</div><div class="desc">Grids of numbers, added and scaled entry by entry</div></div>
<div class="app"><div class="name">Polynomials</div><div class="desc">Expressions like `3x² + x - 1`, added term by term</div></div>
</div>

All three follow the exact same ten rules, even though they look
nothing alike.

---

# Subspace: A Smaller Space Inside a Bigger One

<div class="thread">You rarely need to check all ten rules again. A shortcut exists.</div>

A **subspace** is a subset of a vector space that is itself a vector
space. Check only three things:

1. It contains the zero element
2. Adding any two of its elements stays inside it
3. Scaling any of its elements stays inside it

If all three hold, every other rule holds automatically.

---

# Span: Building a Space From a Few Vectors

<div class="thread">A subspace does not need to be given whole. A few vectors can generate it.</div>

The **span** of a set of vectors is every linear combination of them,
every sum of scaled copies.

```
span{(1, 0)} = every point (a, 0), a any number   -> a line
span{(1, 0), (0, 1)} = every point (a, b)          -> the whole plane
```

A span is always a subspace, no matter which vectors you start from.

---

# The Null Space: All Solutions to `Ax = 0`

<div class="thread">This is exactly last week's open question, answered.</div>

The **null space** of a matrix `A` is every solution to `Ax = 0`,
collected into one set. It is always a subspace.

Last week, the determinant only told us whether that set held one
point, just zero, or many. This week describes the whole set
directly.

---

<!-- SLOT N-2: Worked example -->

# Case Study: The Café's Whole Solution Space

<div class="thread">Back to the pain: describing every working recipe, not just one.</div>

Suppose the cheaper drink keeps only one rule, linking espresso `e`,
milk `m`, and syrup `s`:

```
2e + 4m - 2s = 0
```

One equation, three unknowns. Solve for `e`:

```
e = -2m + s
```

---

# Case Study: Every Recipe at Once

Every solution has this form, for any `m` and `s`:

```
(e, m, s) = m(-2, 1, 0) + s(1, 0, 1)
```

This is a span of two vectors: the null space of the café's rule.
Any `m` and `s` you pick gives one valid recipe ratio. Together, they
describe every working recipe at once, not just the ones staff
happened to try.

<!-- notes: Point out this directly answers the pain slide: the owner
now gets a description of the whole space, not a growing list. -->

---

# The Column Space: What `Ax` Can Reach

<div class="thread">One more space, this time about outputs, not inputs.</div>

The **column space** of `A` is every output `Ax` can produce, as `x`
varies. It answers: which totals `b` even have a solution?

```
Ax = b has a solution   <=>   b is inside the column space of A
```

Null space describes inputs that reach zero. Column space describes
which outputs are reachable at all.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week07/worksheet.html">Worksheet Part A</a>.</div>

Check three sets against the vector space rules. Then find the span
of two small vectors.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. Ask early finishers to explain
which rule failed for any "no" answer. -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: check your Worksheet A answer, then Quiz 1.</div>

---

<!-- NEW: Key Words for 차시 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Homogeneous system:** a system where every equation equals zero, like `Ax = 0`
- **Particular solution:** one specific answer to a system
- **General solution:** every answer, written as a particular solution plus the null space

---

# Describing a Whole Solution Space

<div class="thread">One method also covers systems that are not equal to zero.</div>

For `Ax = b`, every solution has this form:

```
x = (one particular solution) + (any null space vector)
```

Find one working recipe, then add the whole null space to it. That
describes every solution at once, which is exactly this week's
driving question.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week07/worksheet.html">Worksheet Part B</a>.</div>

Describe a small solution space as the span of null space vectors.
Then classify three sets as a subspace or not.

You have about 15 minutes.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

- **Skipping the zero-element check:** a set without a zero element can never be a subspace; check it first
- **Assuming any subset works:** most subsets of a vector space are not subspaces; always test all three rules
- **Confusing span with the starting vectors:** span means every combination, not only the vectors you started with

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Does the set of all `(x, y)` with `y = 2x` form a subspace of R²? Why or why not?
2. What is the span of the single vector `(2, 0)`?

---

# Answers

1. **Yes.** It contains `(0, 0)`, and adding or scaling any point on that line stays on the line.
2. **The x-axis.** Every scalar multiple of `(2, 0)` is a point `(a, 0)`.

---

<!-- NEW: Quiz 1 logistics, before the self-check-quiz hand-off -->

# Quiz 1 Today

<div class="why">Quiz 1 is next: closed-book, covers Weeks 1-7, about 15 minutes.</div>

Put your notes away. Ask any questions now, not during the quiz.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week07/quiz.html">Week 7 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded, and is
separate from today's Quiz 1. It only shows you what you already
know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 9 slot 4 -->

# What This Week's Method Cannot Do Yet

<div class="limits">
We can describe the whole solution space abstractly, as a subspace,
using span, null space, and column space. But we still cannot say how
"big" that space is, or how many independent directions it needs. A
plane and a line are both endless, yet clearly different sizes.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 7 leaves one thing unsolved: **measuring the size of a solution
space, and finding the independent directions inside it.** Week 8
reviews Weeks 1-7 for the midterm. **Week 9, Bases and Dimension**,
then solves it.

---

<!-- SLOT 16: Summary -->

# Summary

- A vector space is a set closed under addition and scaling, plus eight more familiar arithmetic rules
- A subspace only needs three checks: zero element, closed addition, closed scaling
- Span, null space, and column space describe whole solution spaces, not just one answer
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 4
- **Handout:** [materials/week07/handout.md](materials/week07/handout.html), glossary and the full café walkthrough
- **Prepare:** review Weeks 1-7 for the midterm; bring one question about vector spaces to Week 8

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
