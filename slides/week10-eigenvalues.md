---
marp: true
theme: shintia
paginate: true
math: katex
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 10: Eigenvalues

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · Room 610
</div>

<!--
notes: Ask: "Has anyone tried mixing two flavors and the ratio just
would not stay put?" That feeling is today's hook.
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
<div class="wk now"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: we can count directions now; today we find the special ones. -->

---

<!-- SLOT 3: Recap + open wound -->

# Last Week, This Week

- **Last week delivered:** we can count a solution space's independent directions and measure its size.
- **Last week left broken:** we can count independent directions, but not yet find the special directions a transformation stretches without rotating.

<!-- notes: This exact sentence is Week 9's Limit, restated almost verbatim. It becomes today's pain scenario. -->

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), ZERO jargon -->

# The Blend That Never Sits Still

<div class="pain">

The Campus Café buys a new machine. It blends cherry syrup and
vanilla syrup, then mixes the result back through itself again.

The owner wants one starting mix that only gets stronger or weaker
each run. Not shifted sideways toward more cherry, or more vanilla.
Just the same balance, scaled up or down.

Staff try mix after mix. Every single one comes out tilted: a little
more cherry than they put in, or a little more vanilla. Nothing holds
its balance.

The owner asks: "Is there any mix this machine leaves alone, and just
scales?" Nobody on staff can answer that, and nobody knows how to even
start looking for one.

</div>

<!-- notes: Do not say "matrix," "eigenvector," or "transformation" yet. Let the tilted-every-time frustration sit before naming anything. -->

---

# Every Guess Comes Out Tilted

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">Mixes tried by hand</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 20%"></div></div>
  <div class="bar-value">6 tried so far</div>
</div>
<div class="bar-row">
  <div class="bar-label">Mixes that held their balance</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 8%"></div></div>
  <div class="bar-value">0 found</div>
</div>
</div>

Guessing a balanced mix by feel almost never works. More syrups would
only make guessing harder, not easier. This week finds the balanced
mix exactly, without a single trial batch.

<!-- notes: Let the near-empty second bar sit for a second. -->

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Trial batches waste syrup and staff time, every single run
- An engineer who cannot find a system's stable directions may miss a dangerous vibration in a bridge
- A search engine that cannot find "important" pages could not rank results at all
- A robotics team that cannot find a robot arm's stable directions may build a controller that shakes

<div class="why">
<strong>In industry:</strong> Google's original PageRank algorithm
ranks web pages by finding the one steady "importance" pattern an
entire link network settles into. That is an eigenvalue calculation,
run at huge scale. Eigenvalue questions are common in data-science and
engineering interviews.
</div>

---

# Same Idea, Many Fields

<div class="appgrid">
<div class="app"><div class="name">PageRank</div><div class="desc">Finds the one steady "importance" split a whole web of links settles into</div></div>
<div class="app"><div class="name">Vibration analysis</div><div class="desc">Finds the frequencies a bridge or airplane wing naturally shakes at</div></div>
<div class="app"><div class="name">Facial recognition</div><div class="desc">Finds the few directions that describe most of the difference between faces</div></div>
<div class="app"><div class="name">Population models</div><div class="desc">Finds the stable age-group ratio a population settles into over time</div></div>
<div class="app"><div class="name">Robotics &amp; control</div><div class="desc">Finds the directions a robot arm or drone naturally settles toward, or drifts away from</div></div>
</div>

<!-- notes: One line: same shape as the café problem, bigger stakes each time. -->

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"Which directions does a transformation only stretch, never rotate — and by how much?"</div>

---

<!-- NEW: Key Words for Session 1 -->

# Key Words Today

<div class="thread">4 words you will hear all class. Learn them now.</div>

- **Transformation:** a fixed rule that turns one vector into another
- **Direction:** which way a vector points, ignoring how long it is
- **Stretch:** make a vector longer or shorter, without turning it
- **Rotate:** turn a vector to point a new way

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

<style scoped>
.card .h p, .card .d p { margin: 0; }
</style>

<div class="cardlist">
<div class="card"><div class="h">Characteristic Equation</div><div class="d">Find a matrix's eigenvalues using its characteristic equation</div></div>
<div class="card"><div class="h">Find Eigenvectors</div><div class="d">Find the eigenvector that matches each eigenvalue</div></div>
<div class="card"><div class="h">Eigenvector Direction</div><div class="d">Explain why an eigenvector's direction never rotates under its own matrix</div></div>
<div class="card"><div class="h">

Verify $Av = \lambda v$

</div><div class="d">

Check a guessed vector against $Av = \lambda v$, by hand, in seconds

</div></div>
<div class="card"><div class="h">Eigenvectors in PageRank</div><div class="d">Connect eigenvectors to a real system, like PageRank's page ranking</div></div>
</div>

---

<!-- NEW: preview hook, ends Session 1 -->

# Coming Up: Worksheet Part A

Next session, you find the special directions in a real café blend
rule.

Two syrups. One blending rule. You guess first, then solve it
exactly.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- NEW: Key Words for Session 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Eigenvalue:** the number that says how much a special direction stretches or shrinks
- **Eigenvector:** the special direction itself, written as a vector
- **Identity matrix:** a square grid that leaves every vector unchanged; 1s on the diagonal, 0s elsewhere
- **Characteristic equation:** the equation solved to find a matrix's eigenvalues

---

<!-- SLOT 8: Origin -->

# This Problem Is Not New

<div class="thread">You just felt this pain. Others felt it too, long before you.</div>

- **1743, Switzerland:** Leonhard Euler studies a spinning solid body, and finds axes that never wobble as it turns
- **1826, France:** Augustin-Louis Cauchy finds the same kind of special direction inside stressed solid materials
- **1904, Germany:** David Hilbert names the idea *eigenwert*, German for "own value," the root of "eigenvalue" today

<div class="why">
Different fields, same shape: some directions inside a system stay
special, unrotated, no matter what pushes on them. Each field
rediscovered the same pattern before anyone agreed on one shared name
for it.
</div>

---

# Two Hundred Years to a Name

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1743</div><div class="d">Euler<br>rigid-body rotation axes</div></div>
<div class="pt"><div class="dot"></div><div class="y">1826</div><div class="d">Cauchy<br>stress directions in materials</div></div>
<div class="pt"><div class="dot"></div><div class="y">1904</div><div class="d">Hilbert<br>names "eigenwert"</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Search ranking, vibration, face recognition</div></div>
</div>

This idea survived 250 years because the problem, finding a system's
own special directions, never went away.

---

<!-- SLOT 9: Core concept -->

# Eigenvalue & Eigenvector: Definition

<div class="thread">Now the exact, formal definition.</div>

> For a square matrix $A$, an **eigenvector** is a nonzero vector $v$
> that satisfies $Av = \lambda v$ for some number $\lambda$. That matching
> number $\lambda$ is the **eigenvalue**.

- Multiplying $v$ by $A$ only stretches or shrinks it; it never rotates $v$ off its own line
- $v$ must be nonzero; $v = 0$ always solves the equation, but tells us nothing new
- A negative $\lambda$ still keeps the same line, just flips which way $v$ points

---

<!-- Act 3 / BUILD -->

# What "Stretch Without Rotating" Looks Like

<div class="thread">Most starting directions get pushed off course. A few special ones do not.</div>

| Start $v$ | Result $Av$ | What happened |
|---|---|---|
| $(1, 0)$ | $(2, 1)$ | Rotated onto a new line |
| $(1, 1)$ | $(3, 3)$ | Same line, 3 times as long: eigenvalue 3 |
| $(1, -1)$ | $(1, -1)$ | Same line, unchanged: eigenvalue 1 |

Only the last two rows are eigenvectors. The first row shows what
"rotated" looks like, so the contrast is clear.

---

# Guess and Check: Is This Vector an Eigenvector?

<div class="thread">Before solving from scratch, a fast test for any guess.</div>

For $A = \begin{bmatrix} 2 & 1 \\ 1 & 2 \end{bmatrix}$, is $v = (1,1)$ an eigenvector?

$$
Av = \big(2(1)+1(1),\ 1(1)+2(1)\big) = (3, 3) = 3(1,1)
$$

$Av$ is a scalar multiple of $v$. **Yes**, eigenvalue $3$. This check
takes seconds, once you have a candidate to test.

---

# Try It: Quick Eigenvector Check

<div class="why">In pairs, 5 minutes, no worksheet needed yet.</div>

For $A = \begin{bmatrix} 3 & 0 \\ 0 & -1 \end{bmatrix}$, check whether $(1,0)$ and $(1,1)$ are
eigenvectors. Use $Av = \lambda v$ directly, no characteristic equation
needed.

---

# The Characteristic Equation

<div class="thread">One algebra move turns the definition into something we can solve.</div>

Start from the definition and move everything to one side:

$$
\begin{aligned}
Av &= \lambda v \\
Av - \lambda v &= 0 \\
(A - \lambda I)v &= 0
\end{aligned}
$$

For a nonzero $v$ to exist, $(A - \lambda I)$ cannot be invertible. Week 6
showed exactly when that happens: its determinant must be zero.

$$
\det(A - \lambda I) = 0
$$

---

# Eigenvalues Are Roots of a Polynomial

<div class="thread">One more way to see why there is more than one eigenvalue, usually.</div>

Expanding $\det(A - \lambda I)$ for an $n \times n$ matrix always produces a
polynomial in $\lambda$, of degree exactly $n$. This is the **characteristic
polynomial**.

- A degree-$n$ polynomial has at most $n$ roots
- Each root is one eigenvalue; a 2x2 matrix has at most 2, a 3x3 at most 3

---

# Bigger Matrices, Same Idea

<div class="thread">The café's machine is 2x2. The same recipe scales up, in theory.</div>

- The same steps work for any square matrix, not only 2x2
- A 3x3 matrix uses the same cofactor expansion from Week 6, just with more terms to track
- By hand, a 4x4 or larger characteristic equation gets slow fast; a computer runs it instantly

<div class="why">Some matrices have complex-number eigenvalues, a topic outside this course. Every eigenvalue in this week's examples is a plain real number.</div>

---

# Eigenvalues of a Diagonal Matrix

<div class="thread">The easiest possible case, no algebra required.</div>

$$
D = \begin{bmatrix} 5 & 0 \\ 0 & -2 \end{bmatrix}
$$

The eigenvalues are just the diagonal entries themselves: $\lambda = 5$ and
$\lambda = -2$. Each standard-basis vector, $(1,0)$ and $(0,1)$, is already
an eigenvector.

---

# Eigenvalues of a Triangular Matrix

<div class="thread">Week 6's shortcut returns: the diagonal still does the work.</div>

$$
U = \begin{bmatrix} 3 & 4 & 1 \\ 0 & 2 & 5 \\ 0 & 0 & -1 \end{bmatrix}
$$

For any triangular matrix, the eigenvalues are exactly its diagonal
entries: $\lambda = 3, 2, -1$. No characteristic-equation expansion needed.

---

# Negative Eigenvalues: Flipping Direction

<div class="thread">What a negative eigenvalue actually does to a vector.</div>

$Av = -2v$ scales $v$ by $-2$: twice as long, and pointing the
opposite way along the same line.

The direction itself, ignoring which way it points, still never
rotates off its original line. A negative eigenvalue is still a
perfectly valid eigenvalue.

---

# Common Eigenvalue Patterns

<div class="thread">Three shortcuts that connect eigenvalues to tools from earlier weeks.</div>

| Pattern | What it means |
|---|---|
| Any eigenvalue is $0$ | $A$ is singular; $\det(A) = 0$ |
| Sum of all eigenvalues | Equals the **trace** of $A$ (sum of diagonal entries) |
| Product of all eigenvalues | Equals $\det(A)$ |

These hold for every square matrix, not only the café's example.

---

# Demo, Step by Step: The Café's Blend Machine (1/5)

<div class="thread">The exact rule behind the tilted mixes. Let's find its special directions.</div>

Let $c$ and $v$ be the amounts of cherry and vanilla syrup fed in.
The machine's blending rule is:

$$
\begin{aligned}
\text{new } c &= 2c + v \\
\text{new } v &= c + 2v
\end{aligned}
$$

As one matrix $A$:

$$
A = \begin{bmatrix} 2 & 1 \\ 1 & 2 \end{bmatrix}
$$

---

# Demo, Step by Step: The Café's Blend Machine (2/5)

**Build the characteristic equation.** Subtract $\lambda$ from $A$'s
diagonal, then take the determinant:

$$
A - \lambda I = \begin{bmatrix} 2-\lambda & 1 \\ 1 & 2-\lambda \end{bmatrix}
$$

$$
\det(A - \lambda I) = (2-\lambda)(2-\lambda) - (1)(1)
$$

---

# Demo, Step by Step: The Café's Blend Machine (3/5)

**Expand and solve for $\lambda$.**

$$
\begin{aligned}
(2-\lambda)(2-\lambda) - 1 &= 0 \\
\lambda^2 - 4\lambda + 3 &= 0 \\
(\lambda - 1)(\lambda - 3) &= 0
\end{aligned}
$$

Two eigenvalues: $\lambda = 1$ and $\lambda = 3$. Every eigenvector search starts
from one of these.

---

# Demo, Step by Step: The Café's Blend Machine (4/5)

**Find the eigenvector for $\lambda = 3$.** Solve $(A - 3I)v = 0$:

$$
\begin{bmatrix} -1 & 1 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} c \\ v \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

Both rows say the same thing: $c = v$. Pick $c = 1$, so $v = 1$.
Eigenvector: $(1, 1)$, equal cherry and vanilla.

---

# Demo, Step by Step: The Café's Blend Machine (5/5)

**Find the eigenvector for $\lambda = 1$.** Solve $(A - 1I)v = 0$:

$$
\begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix} \begin{bmatrix} c \\ v \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

Both rows say $c = -v$. Eigenvector: $(1, -1)$, equal amounts,
opposite sign. **Check:** $A(1,1) = (3,3) = 3(1,1)$. $A(1,-1) =
(1,-1) = 1(1,-1)$. Both hold.

<!-- notes: The café story is invented; the numbers are picked to
factor evenly. Tell students this out loud: the method is the real,
general one they use on any square matrix, all semester. -->

---

# 3x3 Eigenvalues, Worked (1/3)

<div class="thread">The café's machine was 2x2. Here is the same method, one size up.</div>

For a triangular-friendly example, $A = \begin{bmatrix} 2&1&0 \\ 0&3&0 \\ 0&0&4 \end{bmatrix}$:

$$
A - \lambda I = \begin{bmatrix} 2-\lambda & 1 & 0 \\ 0 & 3-\lambda & 0 \\ 0 & 0 & 4-\lambda \end{bmatrix}
$$

$A$ is already triangular, so $\det(A - \lambda I) = (2-\lambda)(3-\lambda)(4-\lambda)$.

---

# 3x3 Eigenvalues, Worked (2/3)

Set the product to zero:

$$
(2-\lambda)(3-\lambda)(4-\lambda) = 0
$$

Three eigenvalues, one per factor: $\lambda = 2$, $\lambda = 3$, $\lambda = 4$. A
triangular matrix's eigenvalues really are just its diagonal, exactly
as the earlier shortcut slide claimed.

---

# 3x3 Eigenvalues, Worked (3/3)

**Find the eigenvector for $\lambda = 2$.** Solve $(A - 2I)v = 0$:

$$
\begin{bmatrix} 0&1&0 \\ 0&1&0 \\ 0&0&2 \end{bmatrix} \begin{bmatrix} x\\y\\z \end{bmatrix} = \begin{bmatrix} 0\\0\\0 \end{bmatrix}
$$

Rows say $y = 0$ and $z = 0$; $x$ is free. Eigenvector: $(1, 0, 0)$.
Same method as 2x2, just one more row and column to track.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week10/worksheet.html">Worksheet Part A</a>.</div>

A different café machine, a different 2x2 rule.

First guess a balanced mix. Then solve for its real eigenvalues and
eigenvectors.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to check their answer with Av = λv. -->

---

<!-- NEW: Key Words for Session 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Trivial solution:** the always-true but useless answer, $v = 0$
- **Multiplicity:** how many times the same eigenvalue repeats as a root
- **Dominant eigenvalue:** the eigenvalue with the largest size; its direction wins out under repeated use

---

# PageRank: One Page, Explained Simply

<div class="thread">The café's machine had 2 directions. A search engine's "link machine" has millions.</div>

Imagine 4 web pages that link to each other. A page is "important" if
important pages link to it — a circular idea, hard to pin down by
hand.

Google's fix: pass "importance" around the link pattern, over and
over. Eventually the split of importance stops changing.

| Page | Links to | Stable importance share |
|---|---|---|
| A | B, C | 20% |
| B | C | 40% |
| C | A, B, D | 30% |
| D | C | 10% |

<div class="bar-note">illustrative shares, not computed live</div>

---

# PageRank as a Matrix Equation

<style scoped>
.thread p { margin: 0; }
</style>

<div class="thread">

Turn "importance passes around the link pattern" into $Av = \lambda v$.

</div>

Build a matrix $M$ where column $j$ splits page $j$'s importance
evenly across the pages it links to. The stable importance vector $r$
satisfies:

$$
Mr = r \quad = \quad Mr = 1 \cdot r
$$

The stable ranking is exactly an eigenvector of $M$, with eigenvalue
$1$.

---

# PageRank, Worked: A Tiny 2-Page Web (1/2)

<div class="thread">Two pages, A and B. Page A links only to B; page B links only to A.</div>

$$
M = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
$$

Each page sends all of its importance to the other. Solve
$\det(M - \lambda I) = 0$:

$$
(0-\lambda)(0-\lambda) - 1(1) = 0 \;\Rightarrow\; \lambda^2 - 1 = 0 \;\Rightarrow\; \lambda = 1 \text{ or } \lambda = -1
$$

---

# PageRank, Worked: A Tiny 2-Page Web (2/2)

**Find the eigenvector for $\lambda = 1$.** Solve $(M - I)v = 0$:

$$
\begin{bmatrix} -1 & 1 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} a \\ b \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

Both rows say $a = b$. Eigenvector: $(1, 1)$, meaning **equal
importance**. With only two pages linking to each other, that is
exactly the fair result.

---

# Verify PageRank's Eigenvector

<div class="thread">The same check from earlier, applied to the ranking itself.</div>

$$
Mv = \big(0(1)+1(1),\ 1(1)+0(1)\big) = (1, 1) = 1 \cdot (1, 1)
$$

$Mv = v$ holds exactly. Normalized, $(1,1)$ means 50% importance to
each page, the stable split Google's algorithm settles on.

---

# When One Eigenvalue Repeats

<div class="thread">The café's machine gave two clean, different directions. That will not always happen.</div>

For $E = \begin{bmatrix} 3&1\\0&3 \end{bmatrix}$, the characteristic equation is
$(3 - \lambda)^2 = 0$. It has only one root, $\lambda = 3$, but that root counts
twice: its **multiplicity** is 2.

- A repeated eigenvalue can still have just one independent eigenvector direction, not two
- The café's machine avoided this: eigenvalues 3 and 1 are different, each with its own clean direction

---

# Multiplicity: Geometric vs Algebraic

<div class="thread">Two different counts, both called "multiplicity."</div>

- **Algebraic multiplicity:** how many times a root repeats in the characteristic polynomial, $\lambda = 3$ twice for $E$ on the last slide
- **Geometric multiplicity:** how many independent eigenvectors that eigenvalue actually has

For $E = \begin{bmatrix} 3&1\\0&3 \end{bmatrix}$, algebraic multiplicity is 2, but geometric
multiplicity is only 1: one repeated root, one direction.

---

# Case Study: What the Café's Two Directions Mean

<div class="thread">Back to the owner's original question: is there a mix this machine only scales?</div>

- **Direction $(1, 1)$, eigenvalue 3:** equal cherry and vanilla. Every
  run through the machine, this mix triples in strength
- **Direction $(1, -1)$, eigenvalue 1:** equal amounts, opposite sign.
  Every run, this mix stays exactly the same size

Both are the answer the owner asked for: mixes the machine only
scales, never tilts sideways. Any other starting mix, like plain
$(1, 0)$, drifts toward the $(1, 1)$ direction the more times it runs.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week10/worksheet.html">Worksheet Part B</a>.</div>

Check your Part A eigenvectors using $Av = \lambda v$.

Then find the eigenvalues of one 2x2 matrix on your own.

You have about 15 minutes.

---

# Common Mistakes

<style scoped>
.card .h p, .card .d p { margin: 0; }
</style>

<div class="cardlist">
<div class="card"><div class="h">

Forgetting to check $v \neq 0$

</div><div class="d">

$v = 0$ always solves $Av = \lambda v$; it is never a valid eigenvector

</div></div>
<div class="card"><div class="h">

Subtracting $\lambda$ from every entry

</div><div class="d">

$\lambda$ only subtracts from the diagonal entries of $A$, not every entry

</div></div>
<div class="card"><div class="h">

Stopping after finding $\lambda$

</div><div class="d">finding eigenvalues is half the job; each one still needs its own eigenvector</div></div>
<div class="card"><div class="h">Skipping the final check</div><div class="d">

always confirm $Av = \lambda v$ for each pair before trusting the answer

</div></div>
</div>

---

# More Common Mistakes

<div class="cardlist">
<div class="card"><div class="h">Assuming diagonal-only shortcuts work on any matrix</div><div class="d">the "eigenvalues are the diagonal" shortcut only applies to diagonal or triangular matrices</div></div>
<div class="card"><div class="h">Mixing up algebraic and geometric multiplicity</div><div class="d">a repeated root does not guarantee a matching number of independent eigenvectors</div></div>
<div class="card"><div class="h">Forgetting trace and determinant checks</div><div class="d">eigenvalues should always sum to the trace and multiply to the determinant; use this to catch arithmetic mistakes</div></div>
</div>

---

# Check Yourself

1. Is $v = (2, 2)$ an eigenvector of the café's matrix $A = \begin{bmatrix} 2&1\\1&2 \end{bmatrix}$? Which eigenvalue?
2. A matrix's characteristic equation is $\lambda^2 - 5\lambda + 6 = 0$. What are its eigenvalues?
3. Why is $v = (0, 0)$ never a valid eigenvector, even though it solves $Av = \lambda v$ for every $\lambda$?

---

# Answers

1. **Yes.** $(2, 2)$ is $(1, 1)$ scaled by 2, still on the same special
   line. $A(2,2) = (6,6) = 3(2,2)$, so its eigenvalue is 3.
2. **$\lambda = 2$ and $\lambda = 3$.** The equation factors as $(\lambda - 2)(\lambda - 3) = 0$.
3. **It carries no information.** $v = 0$ solves the equation for
   every possible $\lambda$, so it never points to a genuine special
   direction. It is the trivial solution, excluded by definition.

---

# Check Yourself: Round 2

1. $A = \begin{bmatrix} 4&0&0\\0&-1&0\\0&0&2 \end{bmatrix}$. What are its eigenvalues, and why can you read them off directly?
2. A 2x2 matrix has eigenvalues $2$ and $5$. What is its trace? Its determinant?

---

# Answers

1. **$\lambda = 4, -1, 2$.** $A$ is diagonal, so its eigenvalues are exactly its diagonal entries.
2. **Trace = 7, determinant = 10.** Eigenvalues always sum to the trace and multiply to the determinant.

---

# Check Yourself: Round 3

1. A 3x3 matrix's characteristic polynomial has degree 3. At most how many eigenvalues can it have?
2. In the 2-page PageRank example, why did the stable ranking come out as equal importance, $(1,1)$?

---

# Answers

1. **At most 3.** A degree-$n$ characteristic polynomial has at most $n$ roots.
2. **Symmetry.** Each page links only to the other, so nothing favors either page; the eigenvector for $\lambda = 1$ is $(1,1)$, equal shares.

---

# Quick Reference: Eigenvalue Toolkit

| Step | Formula |
|---|---|
| Find eigenvalues | $\det(A - \lambda I) = 0$ |
| Find each eigenvector | $(A - \lambda I)v = 0$, solve for $v$ |
| Sanity check | eigenvalues sum to trace, multiply to $\det(A)$ |
| Final verification | confirm $Av = \lambda v$ directly |

Four steps, the same four steps, on any square matrix.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week10/quiz.html">Week 10 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 11 slot 4 -->

# What Eigenvalues Cannot Do Yet

<div class="limits">
Eigenvalues reveal a matrix's stretch directions, one at a time, by
hand. But real use, like PageRank settling on millions of pages, or a
population model run over many generations, means applying the same
transformation over and over. Repeating that by hand, step by step,
is still completely impractical.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 10 leaves one thing unsolved: **applying a transformation over
and over, fast, instead of one slow step at a time.** By hand, ten
repeats of a blend rule already takes far too long to trust.
**Week 11, Diagonalization**, solves this. It rewrites a matrix using
its own eigenvalues, so repeating it many times becomes one quick
calculation.

---

<!-- SLOT 16: Summary -->

# Summary

- An eigenvector is a direction a matrix only stretches; its eigenvalue says by how much
- Solve $\det(A - \lambda I) = 0$ for eigenvalues, then $(A - \lambda I)v = 0$ for each matching eigenvector
- A repeated eigenvalue has a multiplicity greater than 1, and may share just one eigenvector direction
- Real systems, from search ranking to vibration analysis, hinge on finding these stable directions
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 5.1-5.2
- **Handout:** [materials/week10/handout.md](materials/week10/handout.html), glossary and the full blend-machine walkthrough
- **Prepare:** bring one real situation where repeating a change matters, like compound interest or population growth

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
