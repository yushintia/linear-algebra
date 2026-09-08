---
marp: true
theme: shintia
paginate: true
math: katex
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 4: Matrix Algebra

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · Room 610
</div>

<!--
notes: Ask: "Have you ever had to redo the same two steps for every
single item on a list?" That doubled effort is today's hook.
-->

---

<!-- SLOT 2: Where we are -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk now"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
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

<!-- notes: One sentence: solve, represent, transform, compute, measure, approximate. We are moving from "transform" to "compute efficiently." -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE) -->

# Last Week, This Week

- **Last week delivered:** Week 3 wrote a single change, like a price
  adjustment, as one matrix.
- **Last week left broken:** it could not yet combine two changes into
  one, or undo a change that had already happened.

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE) -->

# One Change at a Time Is Not Enough

<div class="pain">

Last week, the Campus Café wrote one price change as a matrix: a
weekend discount. That worked. One change, one matrix.

This week, the café adds a second change: a delivery surcharge. Both
changes are matrices. But applying two matrices, one after another,
means solving the whole thing twice, for every single order.

Then a register glitch doubles every Saturday price by mistake. The
manager needs to undo just that one change exactly. Nothing so far
shows how to reverse a matrix.

We can describe one transformation as a matrix, but not yet combine or
reverse them.

</div>

<!-- notes: Let the "twice, for every order" line land before moving on. -->

---

# More Changes, More Work

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">1 change, applied once</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 15%"></div></div>
  <div class="bar-value">last week's method works fine</div>
</div>
<div class="bar-row">
  <div class="bar-label">2 changes, discount then surcharge</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 55%"></div></div>
  <div class="bar-value">every order, redone twice</div>
</div>
<div class="bar-row">
  <div class="bar-label">4 changes: discount, surcharge, tax, loyalty</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">redone four times, every order</div>
</div>
</div>

Each new change multiplies the work. This course needs a way to do it
in one step.

---

<!-- SLOT 5: Cost of not knowing -->

# What This Actually Costs

- Redoing every order by hand doubles the work, and doubles the chance of a mistake
- A bigger café, with more daily rules, makes this worse with every new rule
- Without a way to reverse a change exactly, one mistake corrupts every order after it

<div class="why">
<strong>In industry:</strong> image and video editors combine crop,
rotate, and resize into one matrix instead of three slow passes. Game
engines and robots combine motions the same way. "Combine and undo
transformations efficiently" is a common technical interview question.
</div>

---

# Where Combine-and-Reverse Shows Up

<div class="thread">Same idea, many industries. This week's tool is not just for cafés.</div>

<div class="appgrid">
<div class="app"><div class="name">Graphics &amp; Games</div><div class="desc">Camera moves, rotations, and zooms combine into one matrix, once, per frame.</div></div>
<div class="app"><div class="name">Robotics</div><div class="desc">A robot arm combines every joint's rotation into one final position matrix.</div></div>
<div class="app"><div class="name">Software Undo</div><div class="desc">Many undo buttons work because the last action was invertible, so it can be reversed exactly.</div></div>
</div>

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we combine several changes into one step, and undo any one of them exactly?"</div>

---

<!-- NEW: Key Words for Session 1 -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Matrix multiplication:** combining two matrices into one, using a fixed rule
- **Combine:** doing two changes as a single step
- **Inverse:** a matrix that undoes another matrix exactly
- **Identity matrix:** the "do nothing" matrix
- **Order:** the sequence changes happen in

---

<!-- SLOT 7: Learning outcomes -->

# By the End of This Week, You Can

<div class="cardlist">
<div class="card"><div class="h">Matrix Multiplication</div><div class="d">Multiply two matrices to combine two changes into one</div></div>
<div class="card"><div class="h">Non-Commutativity</div><div class="d">Explain why the order of multiplication changes the result</div></div>
<div class="card"><div class="h">Matrix Inverses</div><div class="d">Find a matrix's inverse and use it to undo a change exactly</div></div>
<div class="card"><div class="h">Singular Matrices</div><div class="d">Recognize when a matrix has no inverse</div></div>
</div>

---

<!-- NEW: preview hook, ends Session 1 -->

# Coming Up: Worksheet Part A

Next session, you multiply matrices by hand.

Then you combine two real café price changes into a single matrix,
the same way a real checkout system applies several price rules at
once.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- NEW: Key Words for Session 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Row-by-column:** the exact rule for multiplying two matrices
- **Dimensions:** a matrix's size, rows by columns
- **Square matrix:** a matrix with the same number of rows and columns
- **Commutative:** doing two things in either order gives the same result

---

<!-- SLOT 8: Origin -->

# Where This Idea Came From

<div class="thread">You just felt this pain. One mathematician felt it too, and named the fix.</div>

- **1858, England:** Arthur Cayley publishes *A Memoir on the Theory of Matrices*
- He was tracking what happens when one geometric change is followed by another
- Cayley defined a rule for "multiplying" two matrices so that it matched doing one change, then the other

<div class="why">
His rule also gave matrices an inverse: a way to undo a change, not
just describe it.
</div>

---

# From One Rule to Everyday Computing

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1858</div><div class="d">Cayley<br>defines matrix multiply &amp; inverse</div></div>
<div class="pt"><div class="dot"></div><div class="y">1950s</div><div class="d">Digital computers<br>automate matrix multiplication</div></div>
<div class="pt"><div class="dot"></div><div class="y">1990s</div><div class="d">3D graphics cards<br>chain matrices for every frame</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Deep learning<br>trillions of matrix multiplies, daily</div></div>
</div>

Combining changes into one matrix, then reversing them, is still the
same rule Cayley wrote down.

---

<!-- SLOT 9: Core concept -->

# Matrix Multiplication & Inverse: Definition

<div class="thread">Now the exact, formal definitions.</div>

> **Matrix multiplication** combines matrix `A` and matrix `B` into one
> matrix `AB`, applying `A`'s change, then `B`'s change, in one step.
>
> The **inverse** of a square matrix `A`, written $A^{-1}$, is the matrix
> that undoes `A` exactly.

- Applying `A` then $A^{-1}$ (or $A^{-1}$ then `A`) changes nothing
- Not every matrix has an inverse; this week teaches how to tell

---

<!-- Act 3 / BUILD -->

# Multiplying Two Matrices: The Rule

<div class="thread">One new rule does most of this week's work.</div>

Take each row of the first matrix, and each column of the second.
Multiply matching entries, then add.

---

# Multiplying Two Matrices: A Worked Example

$$
A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} \qquad B = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}
$$

$$
AB = \begin{bmatrix} 1 \times 5 + 2 \times 7 & 1 \times 6 + 2 \times 8 \\ 3 \times 5 + 4 \times 7 & 3 \times 6 + 4 \times 8 \end{bmatrix} = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}
$$

Row 1 of `A` meets column 1 of `B` for the top-left entry, and so on.

---

# Dimensions Must Match

<div class="thread">One rule decides if two matrices can even be multiplied.</div>

A matrix's size is rows $\times$ columns. To multiply `A` times `B`, the
number of columns in `A` must equal the number of rows in `B`.

$$
\begin{aligned}
A \text{ is } 2 \times 3, \ B \text{ is } 3 \times 2 &\to AB \text{ is } 2 \times 2 \text{, this works} \\
A \text{ is } 2 \times 3, \ B \text{ is } 2 \times 2 &\to \text{cannot multiply, } 3 \neq 2
\end{aligned}
$$

Always check sizes first. A mismatch means the multiplication does not
exist at all.

---

# Matrix Times Matrix vs Matrix Times Vector

<div class="thread">Week 3's `Ax` was never a special operation - just a preview of this week.</div>

A vector is really a matrix with one column. Multiplying `A` by a
column vector `x` follows the exact same row-by-column rule as
multiplying two matrices - `x` just happens to be $n \times 1$ instead of
$n \times k$.

$$
\begin{aligned}
A \text{ is } m \times n, \ x \text{ is } n \times 1 &\to Ax \text{ is } m \times 1 \text{, one column} \\
A \text{ is } m \times n, \ B \text{ is } n \times k &\to AB \text{ is } m \times k \text{, } k \text{ columns}
\end{aligned}
$$

---

# Order Matters: AB Is Not BA

<div class="thread">Numbers let you swap order freely. Matrices do not.</div>

$$
A = \begin{bmatrix} 1 & 2 \\ 0 & 1 \end{bmatrix} \qquad B = \begin{bmatrix} 1 & 0 \\ 3 & 1 \end{bmatrix}
$$

$$
AB = \begin{bmatrix} 7 & 2 \\ 3 & 1 \end{bmatrix} \qquad BA = \begin{bmatrix} 1 & 2 \\ 3 & 7 \end{bmatrix}
$$

`AB` and `BA` are different matrices. For matrices, order changes the
answer. Always multiply in the order the problem gives you. This is
why software applies a fixed, documented order for every change.

---

# Order Matters: A Second Example

<div class="thread">One example could be a fluke. Here is a second, different pair.</div>

$$
A = \begin{bmatrix} 2 & 1 \\ 0 & 1 \end{bmatrix} \qquad B = \begin{bmatrix} 1 & 3 \\ 2 & 0 \end{bmatrix}
$$

$$
AB = \begin{bmatrix} 4 & 6 \\ 2 & 0 \end{bmatrix} \qquad BA = \begin{bmatrix} 2 & 4 \\ 4 & 2 \end{bmatrix}
$$

Different matrices again. $AB \neq BA$ is the rule, not the exception.

---

# Matrix Multiplication and the Distributive Rule

<div class="thread">One property numbers and matrices do share.</div>

$$
A(B + C) = AB + AC
$$

For $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$, $B = \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}$, $C = \begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix}$:

$$
\begin{aligned}
A(B + C) &= A \times I = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix} \\
AB + AC &= \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix} + \begin{bmatrix} 0 & 1 \\ 0 & 1 \end{bmatrix} = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}
\end{aligned}
$$

Both sides match. Distributing over addition still works, even
though swapping order does not.

---

# Multiplying Three Matrices: Does Grouping Matter?

<div class="thread">One more property, before moving to the inverse.</div>

$$
(AB)C = A(BC)
$$

Grouping does not matter, only left-to-right order does. This is why
the café can compute $M = S \times D$ once, store just `M`, and never
worry about which pair was multiplied first.

---

# The Identity Matrix: Doing Nothing

<div class="thread">One special matrix changes nothing at all.</div>

$$
I = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}
$$

Multiplying any matrix by `I` leaves it unchanged:

$$
AI = A \qquad IA = A
$$

`I` plays the same role `1` plays in ordinary multiplication. Every
square matrix has its own identity matrix, always 1s down the
diagonal.

---

# The Identity Matrix for Any Size

<style scoped>
.thread p { margin: 0; }
</style>

<div class="thread">

The $2 \times 2$ identity is just the smallest example.

</div>

$$
I = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
$$

Every square matrix, of any size, has its own identity: 1s down the
diagonal, 0s everywhere else. The pattern never changes.

---

# Powers of a Matrix: $A^2$ Means $A \times A$

<div class="thread">Applying the same change twice, written compactly.</div>

For the shear matrix $A = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$:

$$
A^2 = A \times A = \begin{bmatrix} 1 & 2 \\ 0 & 1 \end{bmatrix}
$$

$A^2$ shears twice as far as `A` alone. Just like ordinary numbers,
$A^3 = A \times A \times A$, and so on.

---

# The Inverse: Undoing a Matrix

<div class="thread">Now the tool this week has been missing: how to reverse a matrix.</div>

> A square matrix `A` has an **inverse** $A^{-1}$ when

$$
A \times A^{-1} = I \qquad A^{-1} \times A = I
$$

- Only a square matrix, same number of rows and columns, can have an inverse
- Not every square matrix has one; a matrix with no inverse is called **singular**

---

# Special Cases: Identity and Zero Matrices

<div class="thread">Two matrices worth knowing by sight.</div>

- `I` is its own inverse: $I \times I = I$
- A matrix of all zeros is always singular: anything times an all-zero matrix gives all zeros, and can never reach `I`

---

# Finding a $2 \times 2$ Inverse

<style scoped>
.thread p { margin: 0; }
</style>

<div class="thread">

A short formula finds the inverse of any $2 \times 2$ matrix.

</div>

$$
\text{For } A = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \qquad A^{-1} = \frac{1}{ad-bc} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}
$$

This only works when `ad - bc` is not zero. Week 6 gives this number a
full name and method: the **determinant**.

$$
A = \begin{bmatrix} 3 & 2 \\ 1 & 1 \end{bmatrix} \qquad ad-bc = 3 \times 1 - 2 \times 1 = 1
$$

$$
A^{-1} = \begin{bmatrix} 1 & -2 \\ -1 & 3 \end{bmatrix}
$$

Check by multiplying $A \times A^{-1}$. The result is `I`.

---

# Verifying an Inverse by Multiplying Back

<div class="thread">The previous slide said "check." Here is the check, in full.</div>

$$
A \times A^{-1} = \begin{bmatrix} 3 & 2 \\ 1 & 1 \end{bmatrix} \times \begin{bmatrix} 1 & -2 \\ -1 & 3 \end{bmatrix} = \begin{bmatrix} 3(1)+2(-1) & 3(-2)+2(3) \\ 1(1)+1(-1) & 1(-2)+1(3) \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}
$$

Every entry lands exactly where `I` needs it. This is the whole point
of an inverse: multiply it in, and everything cancels back to `I`.

---

# A Second $2 \times 2$ Inverse Example

<div class="thread">One example could be a fluke. Try the formula on a new matrix.</div>

$$
A = \begin{bmatrix} 4 & 3 \\ 3 & 2 \end{bmatrix} \qquad ad-bc = 4 \times 2 - 3 \times 3 = -1
$$

$$
A^{-1} = \frac{1}{-1} \begin{bmatrix} 2 & -3 \\ -3 & 4 \end{bmatrix} = \begin{bmatrix} -2 & 3 \\ 3 & -4 \end{bmatrix}
$$

Check: $A \times A^{-1} = I$ (confirm this yourself, the same way as the
previous slide).

---

<!-- SLOT N-2: Worked example -->

# Case Study: Two Price Changes as Matrices

<div class="thread">Back to the café. Last week wrote one change as a matrix. Now there are two.</div>

Friday prices, Latte and Mocha, as a price vector:

$$
p = \begin{bmatrix} 800 \\ 900 \end{bmatrix}
$$

Weekend discount `D` (10% off Latte, 5% off Mocha):

$$
D = \begin{bmatrix} 0.90 & 0 \\ 0 & 0.95 \end{bmatrix}
$$

Delivery surcharge `S` (adds 10% of the Latte price onto Mocha):

$$
S = \begin{bmatrix} 1.00 & 0 \\ 0.10 & 1 \end{bmatrix}
$$

---

# Case Study: Combining Them Into One Step

<div class="thread">Multiply the two matrices once. Reuse the result on every order.</div>

Multiply `S` and `D` to get one combined matrix `M`:

$$
M = S \times D = \begin{bmatrix} 0.90 & 0 \\ 0.09 & 0.95 \end{bmatrix}
$$

Apply `M` to Friday's prices, in one step:

$$
M \times p = \begin{bmatrix} 720 \\ 927 \end{bmatrix}
$$

Same answer as applying `D`, then `S`, separately. One multiplication
now replaces two full passes over every order.

---

# Case Study: Why Order Matters Here

<div class="thread">The café's rule is discount first, then surcharge. Swap it, and the price changes.</div>

$$
S \times D = \begin{bmatrix} 0.90 & 0 \\ 0.09 & 0.95 \end{bmatrix} \qquad D \times S = \begin{bmatrix} 0.90 & 0 \\ 0.095 & 0.95 \end{bmatrix}
$$

The two combined matrices are not the same. Applying the surcharge
first, then the discount, gives a slightly different final price.

The café's policy fixes the order: discount first, always. Matrix
order must match business order.

---

# Case Study: Reusing M for Saturday's Prices

<div class="thread">This is why combining into `M` was worth doing in the first place.</div>

Saturday's base prices rose slightly: `p = [850, 950]`. Reuse the same
combined matrix `M`, no re-multiplying `S` and `D`:

$$
M \times p = \begin{bmatrix} 0.90 \times 850 \\ 0.09 \times 850 + 0.95 \times 950 \end{bmatrix} = \begin{bmatrix} 765 \\ 979 \end{bmatrix}
$$

One stored matrix, applied to any day's prices, instantly.

---

# Case Study: Undoing the Combined Discount

<div class="thread">Combining and reversing, together, on the same matrix.</div>

Friday's discounted prices were `[720, 927]`. Find $M^{-1}$ and apply it
to recover the original prices before any change:

$$
M^{-1} \approx \begin{bmatrix} 1.111 & 0 \\ -0.105 & 1.053 \end{bmatrix} \qquad M^{-1} \times \begin{bmatrix} 720 \\ 927 \end{bmatrix} = \begin{bmatrix} 800 \\ 900 \end{bmatrix}
$$

Friday's original prices, `[800, 900]`, come back exactly.

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week04/worksheet.html">Worksheet Part A</a>.</div>

Multiply two small matrices by hand. Then combine two café price
changes into one matrix.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to check by applying the two original matrices separately and comparing. -->

---

# Try It: Quick Multiply Check

<div class="why">Same pairs, two minutes.</div>

Write down any $2 \times 2$ matrix `A` and any $2 \times 2$ matrix `B`. Compute `AB` by
hand while your partner computes `BA`. Compare - they should differ.

---

<!-- NEW: Key Words for Session 3 -->

# Key Words Today

<div class="thread">3 words for the last part of this week.</div>

- **Invertible matrix:** a matrix that has an inverse
- **Singular matrix:** a matrix with no inverse
- **Verify:** check an answer by multiplying it back

---

# Using the Inverse to Undo a Mistake

<div class="thread">Now reverse a matrix. Undo the register glitch exactly.</div>

The register glitch doubled every Saturday price by mistake:

$$
G = \begin{bmatrix} 2 & 0 \\ 0 & 2 \end{bmatrix} \qquad \text{Saturday's wrong prices, } G \times p = \begin{bmatrix} 1600 \\ 1800 \end{bmatrix}
$$

Find $G^{-1}$ and apply it to undo the glitch exactly:

$$
G^{-1} = \begin{bmatrix} 0.5 & 0 \\ 0 & 0.5 \end{bmatrix} \qquad G^{-1} \times (G \times p) = \begin{bmatrix} 800 \\ 900 \end{bmatrix}
$$

Friday's correct prices are back, exactly, with no re-typing.

---

# Case Study: A Second Register Glitch

<div class="thread">A different mistake, the same fix.</div>

This time, the register undercharged every Sunday price by half:

$$
H = \begin{bmatrix} 0.5 & 0 \\ 0 & 0.5 \end{bmatrix} \qquad \text{Sunday's wrong prices, } H \times p = \begin{bmatrix} 400 \\ 450 \end{bmatrix}
$$

Find $H^{-1}$ and undo it:

$$
H^{-1} = \begin{bmatrix} 2 & 0 \\ 0 & 2 \end{bmatrix} \qquad H^{-1} \times (H \times p) = \begin{bmatrix} 800 \\ 900 \end{bmatrix}
$$

Same method, different glitch, the same exact recovery.

---

# The Inverse Also Solves Ax = b

<div class="thread">Week 1 solved this by hand. The inverse solves it in one line.</div>

Week 1's Latte and Mocha system, as a matrix equation:

$$
A = \begin{bmatrix} 2 & 1 \\ 1 & 3 \end{bmatrix} \qquad x = \begin{bmatrix} m \\ s \end{bmatrix} \qquad b = \begin{bmatrix} 800 \\ 900 \end{bmatrix}
$$

Instead of row reduction, multiply both sides by $A^{-1}$:

$$
x = A^{-1} b = \begin{bmatrix} 300 \\ 200 \end{bmatrix}
$$

Same answer Week 1 found by hand: `m = 300`, `s = 200`.

---

# Not Every Matrix Can Be Undone

<div class="thread">One warning before you trust the inverse formula.</div>

$$
A = \begin{bmatrix} 2 & 4 \\ 1 & 2 \end{bmatrix} \qquad ad - bc = 2 \times 2 - 4 \times 1 = 0
$$

$ad - bc = 0$, so $A^{-1}$ does not exist. `A` is **singular**.

- This matches Week 1's "no unique solution" case: a singular matrix's system has none, or infinitely many, solutions
- Week 6's determinant gives an exact test for this, for any size matrix

---

# Quick Recap: Combine, Then Reverse

| Task | Tool | This week's example |
|---|---|---|
| Combine several changes | multiply matrices, in order | discount, then surcharge, into `M` |
| Reverse one change | multiply by its inverse | undoing the register glitch |

Two new operations, one for each half of this week's question.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

<style scoped>
.card .d p { margin: 0; }
</style>

<div class="cardlist">
<div class="card"><div class="h">Assuming AB = BA</div><div class="d">matrix order changes the answer; check the café's discount and surcharge example again</div></div>
<div class="card"><div class="h">Multiplying entry-by-entry</div><div class="d">matrix multiplication is row-by-column, not lining up matching spots</div></div>
<div class="card"><div class="h">Ignoring a size mismatch</div><div class="d">columns of the first matrix must match rows of the second; always check first</div></div>
<div class="card"><div class="h">Assuming every matrix has an inverse</div><div class="d">

always check $ad - bc \neq 0$ before trusting $A^{-1}$

</div></div>
</div>

---

# Common Mistake, Worked: Assuming AB = BA

<div class="thread">Seeing the failure numerically, one more time.</div>

$$
A = \begin{bmatrix} 1 & 2 \\ 0 & 1 \end{bmatrix} \qquad B = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
$$

$$
AB = \begin{bmatrix} 2 & 1 \\ 1 & 0 \end{bmatrix} \qquad BA = \begin{bmatrix} 0 & 1 \\ 1 & 2 \end{bmatrix}
$$

Every entry differs except one. Never assume `AB = BA` without
checking - here, it simply is not true.

---

# Common Mistake, Worked: Trusting the Inverse Formula Blindly

<div class="thread">The formula does not warn you. You have to check first.</div>

$$
A = \begin{bmatrix} 2 & 4 \\ 1 & 2 \end{bmatrix} \qquad ad - bc = 2 \times 2 - 4 \times 1 = 0
$$

Plugging into $\frac{1}{ad-bc}$ divides by zero - the formula breaks
silently if you do not check $ad - bc \neq 0$ first. `A` is singular; no
inverse exists to find.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week04/worksheet.html">Worksheet Part B</a>.</div>

Find an inverse, then use it to solve a small system and undo a price
change.

You have about 15 minutes.

---

# Try It: Predict Before You Compute

<div class="why">Same pairs, five minutes.</div>

Before computing anything, guess: will `AB` equal `BA` for your two
Worksheet Part B matrices? Then compute both and check your guess.

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. `A` is $2 \times 3$ and `B` is $3 \times 4$. What size is `AB`?
2. For $A = \begin{bmatrix} 2 & 0 \\ 0 & 3 \end{bmatrix}$ and $B = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$, is `AB` equal to `BA`?

---

# Answers

1. `AB` is $2 \times 4$. Its size is rows of `A` by columns of `B`.
2. **No.** $AB = \begin{bmatrix} 2 & 2 \\ 0 & 3 \end{bmatrix}$, but $BA = \begin{bmatrix} 2 & 3 \\ 0 & 3 \end{bmatrix}$. The top-right entry differs, so order matters here too.

---

# Check Yourself: Round 2

3. For the identity matrix `I` and any matrix `B` of matching size,
   what is `IB`?
4. Is the all-zero matrix ever invertible? Why or why not?

---

# Answers: Round 2

3. **`IB = B`.** The identity matrix changes nothing, on either side.
4. **No.** Multiplying the zero matrix by anything always gives the
   zero matrix, which can never equal `I`.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week04/quiz.html">Week 4 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT N+1: Limits (Act 4 / CLOSE), becomes Week 5 slot 4 -->

# What Matrix Algebra Cannot Do Yet

<div class="limits">
We can multiply and invert matrices, but for large systems this is
still just slow arithmetic. Combining and reversing changes works, but
computing them by hand does not scale. A café with hundreds of orders
and dozens of rules needs a faster way to actually do this arithmetic,
not just a compact way to write it.
</div>

---

<!-- SLOT N+2: Bridge -->

# Next Week

Week 4 leaves one thing unsolved: **large systems are still slow to
compute by hand.** **Week 5, Factorization**, addresses it. It breaks a
matrix into simpler pieces that make solving much faster. This matters
most once a system has dozens, or hundreds, of unknowns.

---

<!-- SLOT N+3: Summary -->

# Summary

- Matrix multiplication combines two changes into one step; order changes the result
- A matrix's inverse undoes it exactly, and also solves `Ax = b` directly
- Not every matrix has an inverse; a matrix with `ad - bc = 0` is singular
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 2.1-2.3
- **Handout:** [materials/week04/handout.md](materials/week04/handout.html), glossary and the full café walkthrough
- **Reminder:** Assignment 1 is due this week
- **Prepare:** think of one time redoing a task twice felt slower than once. Bring it to Week 5

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
