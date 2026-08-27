---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 3: Linear Transformation

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "Has anyone resized or rotated a picture in an app?" That
everyday action is today's real subject, just written with a matrix.
-->

---

<!-- SLOT 2: Where we are -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk now"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
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

<!-- notes: One sentence: solve, represent, transform, compute, measure, approximate. We are on step 3, transform. -->

---

<!-- SLOT 3: Recap + open wound -->

# Last Week, This Week

- **Last week delivered:** Last week wrote the whole recipe system
  compactly, as `Ax = b`, one line instead of many equations
- **Last week left broken:** It said nothing about whether a matching
  recipe exists for a new order, or whether it is the only one

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), zero jargon -->

# Two Baristas, Two Different Answers

<div class="pain">

A regular customer asks for an exact total taste score, using three
ingredients. The café wants to hit that number exactly, not just get
close.

One barista tries a set of amounts and lands close, but not exact.
A second barista tries different amounts and also lands close, in a
different way.

Neither barista knows whether an exact match is even possible. And if
it is possible, neither knows whether there might be several correct
recipes, not just one.

The two baristas argue about whose method is right. Nobody has a way
to settle it.

</div>

<!-- notes: Do not say "matrix," "solution," or "linear transformation" yet. Let the disagreement sit uncomfortably first. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Time wasted arguing over recipes nobody can confirm or rule out
- An engineer who cannot tell if a design meets its target may
  build the wrong thing
- A photo or design app that resizes a logo unevenly, or flips it by
  mistake, breaks the client's brand

<div class="why">
<strong>In industry:</strong> game engines, photo editors, and design
software all build a shape's transform as a matrix first. Reading a
matrix as "what it does to a shape" is common ground in graphics and
robotics interviews.
</div>

---

# Where Transformations Show Up

<div class="thread">The same matrix idea, across many industries.</div>

<div class="appgrid">
<div class="app"><div class="name">Photo Editing</div><div class="desc">resize, rotate, or flip an image with one matrix</div></div>
<div class="app"><div class="name">Video Games</div><div class="desc">every character and camera move is a matrix</div></div>
<div class="app"><div class="name">Robotics</div><div class="desc">each robot arm joint applies a rotation matrix</div></div>
<div class="app"><div class="name">Computer Vision</div><div class="desc">straightens a tilted, scanned document</div></div>
<div class="app"><div class="name">3D Design</div><div class="desc">moves and resizes objects in a 3D scene</div></div>
<div class="app"><div class="name">Data Science</div><div class="desc">reshapes data to remove hidden overlap</div></div>
</div>

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"What does a matrix actually do to a vector, and how do we build one from a simple rule?"</div>

---

<!-- Key Words for 차시 1 -->

# Key Words Today

<div class="thread">4 words you will hear all class. Learn them now.</div>

- **Transformation:** a rule that takes a vector in and gives a vector out
- **Linear transformation:** a transformation that keeps the origin fixed and keeps straight lines straight
- **Transformation matrix:** the one fixed matrix that carries out a linear transformation
- **Image (of a vector):** the vector you get out, after the transformation

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

<div class="cardlist">
<div class="card"><div class="h">Matrices as Functions</div><div class="d">Explain what a matrix does to an input vector</div></div>
<div class="card"><div class="h">Build a Transformation</div><div class="d">Build a transformation matrix from a plain-English rule</div></div>
<div class="card"><div class="h">Recognize Transformations</div><div class="d">Recognize scaling, rotation, reflection, and shear from their matrices</div></div>
<div class="card"><div class="h">Linearity Test</div><div class="d">Tell whether a given rule is a linear transformation or not</div></div>
</div>

---

<!-- SLOT 8: Origin -->

# Where This Idea Came From

<div class="thread">Turning a rule into a grid of numbers is not new either.</div>

- **1844, Germany:** Hermann Grassmann writes down general rules for
  combining and scaling directions in space, the first formal theory
  of linear transformations
- **1858, England:** Arthur Cayley writes a transformation as a square
  grid of numbers, and defines how to combine two of them

<div class="why">
Cayley's grids are today's matrices. His rule for combining two
transformations becomes matrix multiplication, next week's topic.
</div>

---

# From Grassmann's Rules to Your Screen

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1844</div><div class="d">Grassmann<br>general rules for linear transformations</div></div>
<div class="pt"><div class="dot"></div><div class="y">1858</div><div class="d">Cayley<br>transformations written as matrices</div></div>
<div class="pt"><div class="dot"></div><div class="y">1963</div><div class="d">Sketchpad<br>first interactive computer graphics</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Every photo filter and game<br>uses the same matrix idea</div></div>
</div>

This idea moved from pure geometry to every screen you touch, without
changing its core rule.

---

<!-- SLOT 9: Core concept -->

# Linear Transformation: Definition

<div class="thread">Now the exact, formal definition.</div>

> A **linear transformation** `T` takes a vector in and gives a vector
> out. For any vectors `u`, `v` and any number `c`, it must satisfy:
>
> ```
> T(u + v) = T(u) + T(v)
> T(cu)    = c · T(u)
> ```

- Every linear transformation of this kind can be written as `T(x) = Ax`, for one fixed matrix `A`
- That matrix `A` is the transformation matrix

---

# What Makes a Transformation Linear

<div class="thread">The definition just given draws a sharp line. Here it is.</div>

| Linear | Not linear |
|---|---|
| Scale every point by 2 | Shift every point right by 1 (moves the origin) |
| Swap the two coordinates | Square the x-coordinate (breaks the scaling rule) |
| Rotate every point 90° | Add 3 to every coordinate (moves the origin) |

Only linear transformations are in this course. Every one of them can
be written as a single matrix.

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts by treating a matrix as a machine.</div>

---

<!-- Key Words for 차시 2 -->

# Key Words Today

<div class="thread">5 words for this session: matrix shapes and one building block.</div>

- **Scaling:** stretching or shrinking every vector by the same factor
- **Rotation:** turning every vector by the same angle around the origin
- **Reflection:** flipping every vector across a line, like a mirror
- **Shear:** sliding one direction more than the other, tilting a shape
- **Standard basis vector:** one of the simple "one step" vectors, like `(1, 0)` or `(0, 1)`

---

<!-- Act 3 / BUILD -->

# A Matrix Is a Machine

<div class="thread">Reread last week's Ax = b with new eyes.</div>

<div class="pipeline">
<div class="stage"><div class="h">Input</div><div class="s">vector x</div></div>
<div class="arrow">&rarr;</div>
<div class="stage"><div class="h">Matrix A</div><div class="s">the machine, the fixed rule</div></div>
<div class="arrow">&rarr;</div>
<div class="stage"><div class="h">Output</div><div class="s">vector Ax</div></div>
</div>

Last week, `Ax = b` was a compact way to write a system. This week,
read `A` as a machine. Feed it any input `x`, and it always returns
one exact output.

---

# Matrix Times Vector, Step by Step

<div class="thread">One mechanic runs every example this week.</div>

For any 2x2 matrix and any input vector:

```
[ a  b ]   [ x ]   [ a·x + b·y ]
[ c  d ] × [ y ] = [ c·x + d·y ]
```

Each output number comes from one row of the matrix, matched term by
term with the input vector.

Example, applying `[ 2 1 ; 3 0 ]` to `(4, 1)`:

```
[ 2  1 ]   [ 4 ]   [ 9  ]
[ 3  0 ] × [ 1 ] = [ 12 ]
```

---

# Finding the Matrix from a Rule

<div class="thread">Every transformation matrix hides in two simple test inputs.</div>

Rule: "Double the x-coordinate. Triple the y-coordinate."

Feed in the two standard basis vectors, one at a time:

```
T(1, 0) = (2, 0)
T(0, 1) = (0, 3)
```

Each result becomes one column of the matrix:

```
    [ 2  0 ]
A = [ 0  3 ]
```

The first column is always where `(1, 0)` lands. The second column is
always where `(0, 1)` lands.

---

# A Second Example: Building a Rotation Matrix

<div class="thread">Same method, a different rule.</div>

Rule: "Turn every point a quarter turn, counter-clockwise."

Feed in the two standard basis vectors:

```
T(1, 0) = (0, 1)
T(0, 1) = (-1, 0)
```

Each result becomes one column:

```
    [ 0  -1 ]
A = [ 1   0 ]
```

Reflection and shear, on the next slide, are built the exact same way:
test the two basis vectors, then read off the columns.

---

# Common Geometric Transformations

<div class="thread">Four everyday moves, each just one matrix.</div>

| Transformation | Matrix row |
|---|---|
| **Scaling** — stretches x by 2, y by 3 | `[ 2  0 ]` |
| | `[ 0  3 ]` |
| **Rotation** — quarter turn, counter-clockwise | `[ 0 -1 ]` |
| | `[ 1  0 ]` |
| **Reflection** — flips over the x-axis | `[ 1  0 ]` |
| | `[ 0 -1 ]` |
| **Shear** — tilts the top sideways | `[ 1  1 ]` |
| | `[ 0  1 ]` |

---

<!-- Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week03/worksheet.html">Worksheet Part A</a>.</div>

Given a plain-English rule, build the 2x2 matrix that carries it out.

Then apply your matrix to two sample points by hand.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to check their matrix on the origin: it must map to (0, 0). -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: the same matrix idea, in a logo and in a recipe.</div>

---

<!-- Key Words for 차시 3 -->

# Key Words Today

<div class="thread">4 words for the last part of this week.</div>

- **Unit square:** the square with corners `(0,0)`, `(1,0)`, `(0,1)`, `(1,1)`, used to see a transformation's effect at a glance
- **Order vector:** a list of quantities ordered, used as the input to a recipe matrix
- **Preserves the origin:** a required property of every linear transformation; `(0, 0)` must always map to `(0, 0)`
- **Identity transformation:** the transformation that changes nothing; its matrix has columns `(1, 0)` and `(0, 1)`

---

# Seeing a Transformation: The Unit Square

<div class="thread">One square shows what a matrix does to the whole plane.</div>

Apply the shear matrix `[ 1 1 ; 0 1 ]` to the unit square's corners:

```
(0, 0) -> (0, 0)
(1, 0) -> (1, 0)
(0, 1) -> (1, 1)
(1, 1) -> (2, 1)
```

The square tilts into a slanted parallelogram. Every linear
transformation does this: it turns the unit square into some
parallelogram, and stretches the rest of the plane to match.

---

# The Identity Transformation

<div class="thread">The transformation that changes nothing.</div>

Some rules leave every vector exactly where it started. Its matrix
has columns `(1, 0)` and `(0, 1)`:

```
    [ 1  0 ]
I = [ 0  1 ]
```

Check: `I(3, 5) = (1·3 + 0·5, 0·3 + 1·5) = (3, 5)`. The identity
matrix is a linear transformation too, just a very boring one.

---

<!-- SLOT N-2 (part 1): Worked example, industry grounding -->

# Case Study: Resizing the Café's Logo

<div class="thread">The same matrix idea, outside the kitchen.</div>

The café's logo is a small triangle: `A = (1, 0)`, `B = (0, 1)`,
`C = (1, 1)`. A banner needs it exactly twice as big. Apply the
scaling matrix to corner A:

```
[ 2  0 ]   [ 1 ]   [ 2 ]
[ 0  2 ] × [ 0 ] = [ 0 ]    (corner A)
```

The same matrix moves B to `(0, 2)`, and C to `(2, 2)`. One matrix
resizes the whole shape.

<!-- notes: Photo editors and game engines do exactly this: one matrix, applied to every point of a shape, every frame. -->

---

# Case Study: Rotating the Logo

<div class="thread">A second transform, same triangle.</div>

Rotate the café's logo a quarter turn, for a vertical banner. Apply
the rotation matrix to corner A:

```
[ 0  -1 ]   [ 1 ]   [ 0 ]
[ 1   0 ] × [ 0 ] = [ 1 ]    (corner A)
```

The same matrix moves B to `(-1, 0)`, and C to `(-1, 1)`. Same
process, different matrix, different result.

---

<!-- SLOT N-2 (part 2): Worked example, running case study -->

# Case Study: From Orders to Ingredients

<div class="thread">Same recipe as Week 2, now read as a transformation.</div>

One Regular cup needs 2 units milk, 1 unit syrup. One Large cup needs
3 units milk, 2 units syrup:

```
    [ 2  3 ]
A = [ 1  2 ]
```

An order of 5 Regular and 3 Large cups is the input vector `x = (5, 3)`:

```
Ax = (2·5 + 3·3, 1·5 + 2·3) = (19, 11)
```

The café needs 19 units of milk and 11 units of syrup. Any order goes
through the same matrix, the same way, every time.

---

# Checking Linearity on the Recipe Matrix

<div class="thread">Proving the definition, not just stating it.</div>

Order 1: 5 Regular, 3 Large. Order 2: 2 Regular, 4 Large. Combined
order: 7 Regular, 7 Large.

```
A(5, 3) = (19, 11)                    (previous slide)
A(2, 4) = (2·2+3·4, 1·2+2·4) = (16, 10)
```

Add the two results: `(19+16, 11+10) = (35, 21)`.

```
A(7, 7) = (2·7+3·7, 1·7+2·7) = (35, 21)
```

Same answer, either way. This is the additivity rule from this week's
definition, proven on a real recipe.

---

<!-- Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week03/worksheet.html">Worksheet Part B</a>.</div>

Apply a given matrix to the unit square's four corners, and sketch the
result.

Then decide: is a listed rule a linear transformation, or not?

You have about 15 minutes.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

- **Assuming any rule is a linear transformation:** it must send the
  origin to itself; "shift every point right by 1" fails this test
- **Mixing up rows and columns:** a matrix's first column is where
  `(1, 0)` lands, not the numbers in its first row
- **Multiplying on the wrong side:** always write the matrix first,
  the input vector second, as `Ax`, not `xA`

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. A transformation doubles the x-coordinate and leaves y unchanged.
   Write its 2x2 matrix.
2. Is "shift every point 1 unit to the right" a linear transformation?
   Why or why not?
3. The matrix `[ 0 1 ; 1 0 ]` swaps a vector's two coordinates. What
   is the image of `(3, 7)`?

---

# Answers

1. **`[ 2 0 ; 0 1 ]`**, meaning `[ 2  0 ]` on top, `[ 0  1 ]` below.
2. **No.** It does not send the origin to itself: `(0, 0)` moves to
   `(1, 0)`. A shift is not a linear transformation.
3. **`(7, 3)`.** Row 1 gives `0·3 + 1·7 = 7`; row 2 gives
   `1·3 + 0·7 = 3`.

---

<!-- Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week03/quiz.html">Week 3 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 4 slot 4 -->

# What Today's Method Cannot Do Yet

<div class="limits">
We can describe one transformation as a matrix, and know exactly what
it does to any input. But we cannot yet combine two transformations
into one, or reverse a transformation to undo it. Both need new
matrix operations: multiplying matrices together, and inverting one.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 3 leaves **combining and reversing transformations** unsolved.
**Week 4, Matrix Algebra**, addresses this: multiplying matrices
combines two transformations into one, and inverting a matrix reverses
one, undoing it back to the original input.

---

<!-- SLOT 16: Summary -->

# Summary

- A linear transformation is a rule, `T(x) = Ax`, that keeps the
  origin fixed and straight lines straight
- A matrix's columns are exactly where the standard basis vectors
  land; that is enough to build any transformation matrix
- Scaling, rotation, reflection, and shear are all just matrices
- **Reading:** Lay, Lay & McDonald, 6th ed., Ch. 1.8-1.9
- **Handout:** [materials/week03/handout.md](materials/week03/handout.html), glossary and the full logo and recipe walkthroughs
- **Prepare:** find one transformation you have seen in an app, photo
  editor, or game, and bring it to Week 4

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
