<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 0:** `(1, 0)` belongs to Set B (`m = 1 ≥ 0`). But
`-1 · (1, 0) = (-1, 0)` does not (`m = -1 < 0`). This shows Set B is
not closed under scalar multiplication before students check it
formally.

**Step 1:**

- **Set A: yes, a vector space.** It is a line through the origin (`(0,0)` satisfies `m+s=0`); adding or scaling any point on it stays on it.
- **Set B: no.** Not closed under scalar multiplication — scaling `(1, 0)` by `-1` leaves the set, as shown in Step 0.
- **Set C: no.** No zero element — `(0, 0)` does not satisfy `m + s = 10`.

**Step 2:**

- `span{(1, 1), (2, 2)} = {(a, a) : a any real number}` — still just one line.
- `span{(1, 0), (0, 2)} = {(a, b) : a, b any real numbers}` — the whole plane.

**Discussion question answer:** `(2, 2)` points in the exact same
direction as `(1, 1)` (it is `2 · (1, 1)`), so it adds no new
direction to the span. The span only grows when a new vector points
somewhere the existing set cannot already reach.

### Part B

**Task 1:**

Solve for `m`: `m = 3e - s`.

`(e, m, s) = (e, 3e - s, s) = e(1, 3, 0) + s(0, -1, 1)`

**Check:** `e = 1`, `s = 1` gives `(e, m, s) = (1, 3, 0) + (0, -1, 1)
= (1, 2, 1)`. Substitute: `3(1) - 2 - 1 = 0`. ✓

**Task 2 classification:**

- **Set 1: subspace.** Contains `(0,0,0)`; closed under addition and scaling (a homogeneous linear equation). It is a plane through the origin.
- **Set 2: not a subspace.** Does not contain `(0,0,0)`, since `0+0+0 ≠ 1`. A plane that misses the origin.
- **Set 3: subspace.** Contains `(0,0,0)`; it is the entire y-z plane, closed under addition and scaling.

**Discussion question answer:** Set 1's equation equals zero
(homogeneous), so it passes through the origin and is a subspace.
Set 2's equation equals a nonzero number, so it is a parallel plane
that misses the origin and fails the zero-element test.
