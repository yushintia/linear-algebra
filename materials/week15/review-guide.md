# Week 15 Review Guide: Final Exam (Weeks 1-14)

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This guide holds the same fourteen review questions as the Week 15
slides, organized by theme, each with a full worked answer. Use it to
study after class; the slides only show the short version.

The final exam covers Weeks 1-14. It is worth 30% of your grade (see
the Week 1 grading table). Questions below are weighted toward Weeks
9-14, the post-midterm material, the same way the exam itself will be.

---

## Theme 1: Solve, Then Represent (Weeks 1-2)

**The arc:** Week 1 solved a system exactly, by hand, using row
operations. Week 2 compacted that same system into one reusable form,
`Ax = b`.

### Question 1 (Week 1)

After elimination, a café system reaches `0 = 5`. What does that tell
you about the solutions?

**Answer:** **No solution.**

`0 = 5` is a false statement, no matter what values the unknowns take.
Reaching it during elimination means the original equations contradict
each other: no combination of values can make every equation true at
the same time.

Contrast this with `0 = 0`, a true statement. That case means one
equation carried no new information, leaving a free unknown and
infinitely many solutions instead. Telling these two outcomes apart,
by checking whether the leftover statement is true or false, is one of
the most commonly confused points from Week 1. Always check which one
you actually reached before reporting an answer.

### Question 2 (Week 2)

Write `2x + 3y = 7`, `4x - y = 1` as `Ax = b`. What are `A` and `b`?

**Answer:**

```
A = [  2   3 ]     x = [ x ]     b = [ 7 ]
    [  4  -1 ]         [ y ]         [ 1 ]
```

Each row of `A` holds one equation's coefficients, in the same order
the unknowns appear: row 1 is `2, 3` from `2x + 3y`, row 2 is `4, -1`
from `4x - y`. `b` holds each equation's number on the right of the
equal sign, in the same row order as `A`.

Check the shape: `A` is 2×2, `x` has 2 entries, so `Ax` has 2 entries,
matching `b`'s 2 entries. This compact form is what every later
week's tools, factorization, determinants, eigenvalues, are built to
operate on.

---

## Theme 2: Transform and Combine (Weeks 3-5)

**The arc:** Week 3 showed that any linear rule becomes one matrix.
Week 4 showed how to combine or undo those matrices. Week 5 showed
how to reuse one factorization instead of re-solving from scratch.

### Question 3 (Week 4)

Find the inverse of `A = [[3,1],[2,1]]`.

**Answer:**

```
A⁻¹ = [  1  -1 ]
      [ -2   3 ]
```

Using the 2×2 inverse formula, `A⁻¹ = 1/(ad-bc) × [[d,-b],[-c,a]]`:
here `a=3, b=1, c=2, d=1`, so `ad - bc = 3(1) - 1(2) = 1`. Dividing by
`1` leaves the swapped-and-negated matrix unchanged:

```
A⁻¹ = 1/1 × [ 1  -1 ]   =   [  1  -1 ]
            [ -2   3 ]      [ -2   3 ]
```

**Check:** multiply `A · A⁻¹` and confirm it gives the identity
matrix:

```
Row 1: 3(1) + 1(-2) = 1,     3(-1) + 1(3) = 0
Row 2: 2(1) + 1(-2) = 0,     2(-1) + 1(3) = 1

A · A⁻¹ = [ 1  0 ]   ✓
          [ 0  1 ]
```

Whenever `ad - bc ≠ 0`, this formula gives a matrix that undoes `A`
exactly, the same idea Week 4 used to undo the register's doubling
glitch.

### Question 4 (Week 5)

`A = [[4,2],[2,3]]` factors as `L = [[1,0],[0.5,1]]`,
`U = [[4,2],[0,2]]`. Solve `Ax = b` for `b = [10, 9]`.

**Answer:** Never re-run elimination on `A` itself; that work is
already saved inside `L` and `U`. Instead, solve two triangular
systems.

**Forward substitution**, solve `Ly = b` top to bottom:

```
1·y1              = 10   ->  y1 = 10
0.5·y1  +  1·y2   = 9    ->  y2 = 9 - 0.5(10) = 4
```

**Back substitution**, solve `Ux = y` bottom to top (`x = [x1, x2]`):

```
2·x2              = 4    ->  x2 = 2
4·x1  +  2·x2     = 10   ->  x1 = (10 - 2(2)) / 4 = 1.5
```

So `x1 = 1.5`, `x2 = 2`. **Check:** `A·x = (4(1.5)+2(2), 2(1.5)+3(2))
= (10, 9) = b`. ✓ If tomorrow brings a different `b`, the same `L`
and `U` solve it again in two quick substitutions, with no new
elimination.

---

## Theme 3: Measure the Solution Space (Weeks 6, 7, 9)

**The arc:** Week 6 checked, before fully solving, whether a system
has exactly one answer. Week 7 described a whole solution space at
once. Week 9 measured how big that space actually is.

### Question 5 (Week 6)

Compute the determinant of `A = [[1,0,2],[0,3,1],[1,1,1]]`.

**Answer:**

```
det = -4
```

Cofactor expansion along row 1 (entries `1, 0, 2`):

```
det = 1 · det[[3,1],[1,1]]  -  0 · det[[0,1],[1,1]]  +  2 · det[[0,3],[1,1]]
```

Each 2×2 minor uses the `ad - bc` rule:

```
det[[3,1],[1,1]] = 3(1) - 1(1) = 2
det[[0,3],[1,1]] = 0(1) - 3(1) = -3
```

Substituting back, remembering the middle term drops out because its
coefficient is `0`:

```
det = 1(2) - 0 + 2(-3) = 2 - 6 = -4
```

`-4` is nonzero, so a system with this coefficient matrix has exactly
one solution. This check took a few lines, far less than fully
solving a 3×3 system by elimination.

### Question 6 (Week 7)

The café's rule matrix `A` has a null space of dimension 2. What does
that tell you about solutions to `Ax = 0`?

**Answer:** **Infinitely many solutions.**

The null space is the set of every vector `x` satisfying `Ax = 0`. If
its dimension is 2, more than just the zero vector solves the
equation: there is a whole 2-dimensional family of solutions, spanned
by 2 independent vectors.

A null space of dimension 0 would mean only `x = 0` solves `Ax = 0`,
the trivial case. A dimension of 2 instead means 2 unknowns stay
free once the constraints are applied: pick any values for those two,
and a valid solution follows. This connects directly to Week 9's
rank-nullity theorem: a bigger nullity always means more freedom left
in the solution set.

---

## Theme 4: Find Special Directions (Weeks 9-11)

**The arc:** Week 9 counted independent directions and named the
smallest set that spans a space. Week 10 found the specific
directions a matrix only stretches, never rotates. Week 11 reused
those directions to make repeated transformations fast.

### Question 7 (Week 9)

Are `v1 = (1,2,0)`, `v2 = (0,1,1)`, `v3 = (1,4,2)` linearly
independent?

**Answer:** **No, they are dependent.**

Test whether some nonzero combination of the three reaches the zero
vector. Try `v1 + 2v2`:

```
v1 + 2v2 = (1,2,0) + 2(0,1,1) = (1,2,0) + (0,2,2) = (1,4,2)
```

This equals `v3` exactly, so `v1 + 2v2 - v3 = 0` is a nonzero
combination (coefficients `1, 2, -1`) that reaches zero. That is the
definition of a dependent set. Rearranging shows `v3` was never
genuinely new: `v3 = v1 + 2v2`. Only 2 of the 3 vectors, for example
`{v1, v2}`, are needed to span the same space; `v3` adds nothing.

### Question 8 (Week 9)

A 3×5 matrix has rank 3. What is its nullity?

**Answer:** **Nullity = 2.**

The rank-nullity theorem states that for a matrix with `n` columns:

```
rank(A) + nullity(A) = n
```

Here `n = 5` (5 columns, 5 unknowns) and `rank(A) = 3`:

```
3 + nullity = 5   ->   nullity = 2
```

Rank counts how many independent directions the matrix's columns
actually reach; nullity counts how many unknowns stay unconstrained.
Together they always account for every column, constrained or free.

### Question 9 (Week 10)

Find the eigenvalues of `A = [[4,2],[1,3]]`.

**Answer:** **λ = 5 and λ = 2.**

Build the characteristic equation, `det(A - λI) = 0`:

```
A - λI = [ 4-λ    2  ]
         [  1    3-λ ]

det(A - λI) = (4-λ)(3-λ) - (2)(1)
```

Expand and simplify:

```
(4-λ)(3-λ) - 2 = 12 - 4λ - 3λ + λ² - 2 = λ² - 7λ + 10
```

Set this equal to zero and factor:

```
λ² - 7λ + 10 = 0
(λ - 5)(λ - 2) = 0
```

Two eigenvalues: `λ = 5` and `λ = 2`. Every eigenvector search starts
from one of these two numbers.

### Question 10 (Week 10)

Find the eigenvector for `λ = 5`, from Question 9's matrix.

**Answer:** **Eigenvector `(2, 1)`.**

Solve `(A - 5I)v = 0`:

```
A - 5I = [ -1   2 ]
         [  1  -2 ]

[ -1   2 ] [v1]   [0]
[  1  -2 ] [v2] = [0]
```

Both rows say the same thing: `-v1 + 2v2 = 0`, or `v1 = 2v2`. Pick
`v2 = 1`, so `v1 = 2`. Eigenvector: `(2, 1)`.

**Check:** confirm `Av = λv`:

```
A(2,1) = (4(2)+2(1), 1(2)+3(1)) = (10, 5)
5(2,1) = (10, 5)     ✓
```

Both sides match, so `(2, 1)` is a genuine eigenvector for `λ = 5`.

### Question 11 (Week 11)

Question 9's matrix has two different eigenvalues, `5` and `2`. Is it
diagonalizable? Why?

**Answer:** **Yes.**

A matrix is diagonalizable when it has a full set of linearly
independent eigenvectors, one genuinely new direction per row or
column. A key shortcut: **distinct eigenvalues always produce
independent eigenvectors.** Since this matrix's two eigenvalues, `5`
and `2`, are different from each other, their eigenvectors are
automatically independent.

A 2×2 matrix needs exactly 2 independent eigenvectors to diagonalize.
This matrix has exactly that, so `A = PDP⁻¹` holds, with:

```
P = [ 2   v ]     D = [ 5  0 ]
    [ 1   w ]         [ 0  2 ]
```

where `(v, w)` is the eigenvector for `λ = 2` (not computed here).
The risky case, from Week 11, is a *repeated* eigenvalue with too few
independent eigenvectors; that case is not diagonalizable. This
matrix avoids that entirely.

---

## Theme 5: Measure, Then Approximate (Weeks 12-14)

**The arc:** Week 12 measured length, distance, and angle exactly.
Week 13 used that measurement to find the closest point in a
subspace. Week 14 applied the closest-point idea to real, noisy data
that has no exact answer.

### Question 12 (Week 12)

Are `u = (3, -2)` and `v = (4, 6)` orthogonal? Show the dot product.

**Answer:** **Yes, orthogonal.**

```
u · v = (3)(4) + (-2)(6) = 12 - 12 = 0
```

Two vectors are orthogonal exactly when their dot product equals
zero. Here the dot product is `0`, so `u` and `v` meet at a right
angle. This test works in any number of dimensions, even where a
picture is impossible to draw.

### Question 13 (Week 13)

Project `y = (5, 3)` onto the line spanned by `u = (1, 0)`.

**Answer:** **`proj_u(y) = (5, 0)`.**

Apply the projection formula:

```
proj_u(y) = ((y · u) / (u · u)) u
```

Compute each piece:

```
y · u = 5(1) + 3(0) = 5
u · u = 1(1) + 0(0) = 1
proj_u(y) = (5 / 1)(1, 0) = (5, 0)
```

The closest point on the line spanned by `(1, 0)`, the x-axis, to
`(5, 3)` is `(5, 0)`. The leftover part, `z = y - proj_u(y) = (0, 3)`,
forms a right angle with `u`: `z · u = 0(1) + 3(0) = 0`. ✓

### Question 14 (Week 14)

A café survey collects 8 noisy taste ratings, but a line has only 2
unknowns. Why is there no exact solution to `Ax = b`?

**Answer:** **The system is overdetermined: more equations than
unknowns.**

`A` has 8 rows (one per rating) but only 2 columns (slope and
intercept), so `Ax = b` asks 8 equations to agree using only 2 free
values. With real, noisy data, `b` almost never lands exactly inside
the column space of `A`; no choice of `x` makes `Ax` equal `b` on
every point at once.

Least squares does not try to solve this impossible system exactly.
Instead it solves the normal equations, `AᵀAx̂ = Aᵀb`, which always has
a solution. The result `x̂` is the best approximate answer: the one
that minimizes the sum of squared residuals, `||b - Ax̂||²`. This is
exactly last week's projection idea (Week 13), applied to a system
that cannot be solved exactly.

---

## Quick Reference: Where Each Week Fits

| Week | Skill | Key tool |
|---|---|---|
| 1 | Solve a system exactly | Row operations: swap, scale, add |
| 2 | Write a system compactly | `Ax = b` |
| 3 | Describe one action on vectors | Transformation matrix |
| 4 | Combine and undo actions | Matrix multiplication, inverse |
| 5 | Solve the same system fast, repeatedly | `LU` factorization |
| 6 | Check for a unique solution, before solving | Determinant |
| 7 | Describe a whole solution space | Span, null space, subspace |
| 9 | Count independent directions | Basis, dimension, rank |
| 10 | Find stretch-only directions | Eigenvalues, eigenvectors |
| 11 | Make repeated transformations fast | Diagonalization, `A = PDP⁻¹` |
| 12 | Measure length, distance, angle | Dot product, norm |
| 13 | Find the closest point in a subspace | Projection, orthogonality |
| 14 | Fit the best line to noisy data | Least squares, normal equations |

Study tip: for each row above, close this guide and try to explain
the tool in your own words, then work one problem from that week's
handout without looking at the answer key first. The final exam draws
from all fourteen weeks, weighted toward Weeks 9-14.
