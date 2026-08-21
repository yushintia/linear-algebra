# Week 8 Review Guide: Midterm (Weeks 1-7)

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This guide holds the same ten review questions as the Week 8 slides,
organized by week, each with a full worked answer. Use it to study
after class; the slides only show the short version.

The midterm covers Weeks 1-7 only. It is worth 30% of your grade (see
the Week 1 grading table).

---

## Week 1: Linear Systems

**Driving question:** "How do we solve many linked equations at once,
exactly, without guessing?"

**What you should now be able to do:** turn a real scaling problem
into a system of equations; use row operations (swap, scale, add) to
solve any system exactly; tell whether a system has one solution,
many, or none.

### Question 1

After elimination, two of the café's three rules stay independent.
The third becomes `0 = 0`. What does that tell you about the
solutions?

**Answer:** There are **infinitely many solutions**.

`0 = 0` is always true, no matter what values the unknowns take. That
means the third rule carried no new information; it was already
implied by the other two. With only two independent rules left, but
three unknowns, one unknown stays free: pick any value for it, and the
other two are then determined. A free unknown always means infinitely
many solutions, not zero and not exactly one.

Contrast this with `0 = 5`: a false statement instead of a true one.
That case means no solution at all, because the equations contradict
each other. The difference between `0 = 0` (infinitely many) and
`0 = 5` (none) is one of Week 1's most commonly confused points —
always check which one you actually reached.

---

## Week 2: Vector & Matrix

**Driving question:** "How do we write and solve any linear system in
one compact, computable form?"

**What you should now be able to do:** write any linear system as a
vector, a matrix, and `Ax = b`; multiply a matrix by a vector by hand;
verify a candidate solution by computing `Ax` and comparing it to `b`.

### Question 2

Write `3x - y = 5`, `2x + 4y = 6` as `Ax = b`. What are `A` and `b`?

**Answer:**

```
A = [  3  -1 ]     x = [ x ]     b = [ 5 ]
    [  2   4 ]         [ y ]         [ 6 ]
```

Each row of `A` holds one equation's coefficients, in the same order
the unknowns appear: row 1 is `3, -1` from `3x - y`, row 2 is `2, 4`
from `2x + 4y`. `b` holds each equation's number on the right of the
equal sign, in the same row order as `A`. `x` is always a column
vector holding the unknowns, `x` then `y`.

Check the shape: `A` is 2×2, `x` has 2 entries, so `Ax` has 2 entries,
matching `b`'s 2 entries. If a size mismatch ever shows up, `A`, `x`,
or `b` was written down wrong.

---

## Week 3: Linear Transformation

**Driving question:** "What does a matrix actually do to a vector,
and how do we build one from a simple rule?"

**What you should now be able to do:** build a transformation matrix
from a plain-English rule; recognize scaling, rotation, reflection,
and shear from their matrices; tell whether a rule is a linear
transformation or not.

### Question 3

A rule triples the x-coordinate and flips the sign of y. Write its
2x2 matrix.

**Answer:**

```
    [ 3   0 ]
A = [ 0  -1 ]
```

The fastest way to build any transformation matrix: feed in the two
standard basis vectors, `(1, 0)` and `(0, 1)`, one at a time, and read
off where each one lands.

- `T(1, 0)`: x triples to `3`, y stays `0` (nothing to flip). Result:
  `(3, 0)`. This becomes column 1
- `T(0, 1)`: x stays `0` (nothing to triple), y flips sign to `-1`.
  Result: `(0, -1)`. This becomes column 2

Stack those two results side by side as columns, and the matrix is
done. This "column = where a basis vector lands" trick works for any
linear rule, no matter how it is described in words.

---

## Week 4: Matrix Algebra

**Driving question:** "How do we combine several changes into one
step, and undo any one of them exactly?"

**What you should now be able to do:** multiply two matrices to
combine two changes into one; find a matrix's inverse and use it to
undo a change exactly; recognize a singular matrix, one with no
inverse.

### Question 4

Multiply `A = [[1,2],[3,1]]` and `B = [[2,0],[1,1]]`. Find `AB`.

**Answer:**

```
AB = [ 1(2)+2(1)   1(0)+2(1) ]   [ 4  2 ]
     [ 3(2)+1(1)   3(0)+1(1) ] = [ 7  1 ]
```

Matrix multiplication is row-by-column: take a row of `A`, a column
of `B`, multiply matching entries, then add. The top-left entry of
`AB` comes from row 1 of `A`, `(1, 2)`, times column 1 of `B`,
`(2, 1)`: `1×2 + 2×1 = 4`. Repeat for every row/column pair.

Always check sizes first: `A` is 2×2, `B` is 2×2, so `AB` is defined
and comes out 2×2. Remember `AB` is not generally equal to `BA` — the
order in the problem is the order you must multiply in.

### Question 5

Recall Week 4's register glitch, `G = [[2,0],[0,2]]`. Find `G⁻¹`, and
say what it does.

**Answer:**

```
G⁻¹ = [ 0.5   0  ]
      [  0   0.5 ]
```

Using the 2x2 inverse formula, `A⁻¹ = 1/(ad-bc) × [[d,-b],[-c,a]]`:
here `ad - bc = 2×2 - 0×0 = 4`, so `G⁻¹ = 1/4 × [[2,0],[0,2]]`, which
simplifies to `[[0.5,0],[0,0.5]]`.

`G⁻¹` undoes exactly what `G` did. `G` doubled every price; `G⁻¹`
halves every price back. Multiplying `G⁻¹ × (G × p)` returns the
original price vector `p` exactly, with no re-typing needed. This is
the general pattern: whenever a mistake can be written as "multiply
by some matrix," its inverse undoes the mistake exactly, as long as
that matrix is invertible (`ad - bc ≠ 0`).

---

## Week 5: Factorization

**Driving question:** "If a system's left side never changes, can we
solve it once and reuse that work forever?"

**What you should now be able to do:** factor a matrix `A` into a
lower triangular `L` and an upper triangular `U`; solve a triangular
system quickly, top to bottom or bottom to top; reuse one `LU`
factorization to solve many systems sharing the same left side.

### Question 6

`A = [[2,1],[1,3]]` factors as `L = [[1,0],[0.5,1]]`,
`U = [[2,1],[0,2.5]]`. To solve `Ax = b` for `b = [800, 900]`, which
two steps do you take, in order?

**Answer:** First solve `Ly = b` by **forward substitution**, then
solve `Ux = y` by **back substitution**. Never re-run elimination on
`A` itself — that work is already saved inside `L` and `U`.

**Forward substitution**, solve `Ly = b` top to bottom:

```
1·y1              = 800   ->  y1 = 800
0.5·y1  +  1·y2   = 900   ->  y2 = 900 - 0.5(800) = 500
```

**Back substitution**, solve `Ux = y` bottom to top (`x = [m, s]`):

```
2.5·s             = 500   ->  s = 200
2·m   +  1·s      = 800   ->  m = (800 - 200) / 2 = 300
```

So `m = 300`, `s = 200` — the exact same answer as Week 1's Latte and
Mocha worksheet, and Week 5's own worked example. The whole point of
`LU` factorization: if tomorrow's receipts give a different `b`, the
same `L` and `U` solve it again in two quick substitutions, with no
new elimination.

---

## Week 6: Determinants

**Driving question:** "How can we tell, before fully solving, whether
a system has exactly one answer?"

**What you should now be able to do:** compute the determinant of a
2x2 or 3x3 matrix; use a determinant to decide if a system has exactly
one solution; explain what a zero determinant does, and does not,
tell you.

### Question 7

Compute the determinant of `[[4,1],[2,3]]`.

**Answer:**

```
det = 4(3) - 1(2) = 12 - 2 = 10
```

For any 2x2 matrix `[[a,b],[c,d]]`, the determinant is `ad - bc`.
Here `a=4, b=1, c=2, d=3`, so `det = 4×3 - 1×2 = 10`. Since `10` is
nonzero, a system with this matrix as its coefficient matrix has
exactly one solution — this check took seconds, far less than fully
solving it.

### Question 8

A 3x3 recipe matrix has determinant `0`. Does that mean no solution,
or could it mean many? Explain.

**Answer:** **You cannot tell which, from the determinant alone.**

A zero determinant only tells you one thing for certain: the system
does **not** have exactly one solution. It rules out "unique," but it
does not decide between the two remaining cases:

- **No solution** — the equations contradict each other (elimination
  reaches something like `0 = 5`)
- **Infinitely many solutions** — one equation added no new
  information (elimination reaches `0 = 0`)

To tell which of the two you actually have, you still need to run
elimination (or check the null space, Week 7's tool) and see which
kind of row you end up with. This is exactly the trap in Week 6's
"Mega Cup" pain scenario: a zero determinant flags trouble, but
finding out *what kind* of trouble still takes more work.

---

## Week 7: Vector Spaces

**Driving question:** "How do we describe an entire solution space,
not just one solution?"

**What you should now be able to do:** check whether a set forms a
vector space or a subspace; find the span of a small set of vectors;
describe the whole solution set of `Ax = 0` as a null space.

### Question 9

Does the set of all `(x, y, z)` with `x + y + z = 0` form a subspace
of R³? Why?

**Answer:** **Yes.** Check the three subspace rules:

1. **Contains zero:** `(0, 0, 0)` satisfies `0 + 0 + 0 = 0`. ✓
2. **Closed under addition:** take any two points in the set, say
   `(a1,b1,c1)` and `(a2,b2,c2)`, both summing to zero. Their sum
   `(a1+a2, b1+b2, c1+c2)` also sums to zero, since
   `(a1+b1+c1) + (a2+b2+c2) = 0 + 0 = 0`. ✓
3. **Closed under scaling:** scaling a point that sums to zero by any
   number `k` gives `(ka, kb, kc)`, which sums to `k(a+b+c) = k(0) = 0`.
   Still in the set. ✓

All three rules hold, so the set is a subspace. It is, in fact, a
plane through the origin inside R³ — this exact shape shows up
whenever a single linear equation equals zero, which is always a
subspace (a hyperplane through the origin).

### Question 10

The café's cheaper-drink rule is `2e + 4m - 2s = 0`, which gives
`e = -2m + s`. Write the full solution set as a span of two vectors.

**Answer:**

```
(e, m, s) = m(-2, 1, 0) + s(1, 0, 1)
```

Since `e = -2m + s`, every solution has the form `(-2m+s, m, s)` for
any numbers `m` and `s`. Splitting this into the part scaled by `m`
and the part scaled by `s`:

```
(-2m+s, m, s) = (-2m, m, 0) + (s, 0, s) = m(-2,1,0) + s(1,0,1)
```

This is the **span** of the two vectors `(-2,1,0)` and `(1,0,1)`: the
**null space** of the café's one-equation rule. Pick any `m` and `s`,
and you get one exact working recipe ratio. Together, all the choices
of `m` and `s` describe *every* working recipe at once, answering
Week 7's driving question directly: not one recipe, but the whole
space of recipes, in one compact description.

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

Study tip: for each row above, close this guide and try to explain
the tool in your own words, then work one problem from that week's
handout without looking at the answer key first.
