<!-- page break for print -->

## Professor Answer Key (do not hand out this section)

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

### Part C

**Task 1 (Basis Waveforms):**

`span{(1, 1), (1, -1)} = {(a, b) : a, b any real numbers}`: the
whole plane. `(1,1)` and `(1,-1)` do not point in the same direction,
so together they reach every point in the plane.

**Answer:** No, a single waveform vector cannot span every snippet.
One vector's span is only a line (all its scalar multiples); it
takes at least two non-parallel vectors to reach every point in the
plane, as this task's two waveforms do together.

**Task 2 (Grayscale Subspace and Channel Span):**

- **Set G: yes, a vector space.** It contains `(0,0,0)` (since
  `0=0=0`); adding two grayscale colors, or scaling one, always
  keeps `R=G=B`. It is a line through the origin in R³ (the "gray
  diagonal").
- **Set S: no.** No zero element: `(0,0,0)` gives `0+0+0=0`, not
  `1`.

`span{(1,0,0),(0,1,0)} = {(a, b, 0) : a, b any real numbers}`: the
plane of all colors with zero blue channel.

**Discussion question answer:** `(2,0,0)` points in the exact same
direction as `(1,0,0)` (it is `2·(1,0,0)`), and it has zero blue
channel already, so it adds no new direction. The span stays the
same plane.

**Task 3 (Joint-Angle Calibration Constraint):**

- **Set K: yes, a vector space.** `(0,0)` satisfies
  `0 - 2(0) = 0`; it is a line through the origin, closed under
  addition and scaling.
- **Set L: no.** No zero element: `0 - 2(0) = 0 ≠ 5`.

**Discussion question answer:** Set K's equation equals zero
(homogeneous), so its line passes through the origin and is a vector
space. Set L's equation equals a nonzero number, so it is an offset
(parallel) line that misses the origin and fails the zero-element
test, exactly the same distinction as Set 1 vs. Set 2 in Part B.

**Task 4 (Root Condition and Span):**

**Set R: yes, a vector space.** `(0,0)` satisfies `0+0=0`
(the zero polynomial has `p(1)=0`); it is a homogeneous line through
the origin, closed under addition and scaling.

`span{(1,1),(2,3)}`: check whether `(1,1)` and `(2,3)` point in the
same direction: `1(3) - 1(2) = 1 ≠ 0`, so they do not. Two
non-parallel vectors in R² span all of R², so
`span{(1,1),(2,3)} = {(a,b) : a, b any real numbers}`: every
degree-≤1 polynomial.

**Answer:** Yes, `3 + 2x` (the vector `(3,2)`) is inside this span,
because the span is all of R². Any vector in the plane is reachable
once two non-parallel vectors are available, without needing to
solve for the exact combination.

**Task 5 (Cable Tension Equilibrium):**

Solve for `T2`: `T2 = 2T1 + T3`.

`(T1, T2, T3) = (T1, 2T1 + T3, T3) = T1(1, 2, 0) + T3(0, 1, 1)`

**Check:** `T1 = 1`, `T3 = 1` gives `(T1, T2, T3) = (1, 2, 0) +
(0, 1, 1) = (1, 3, 1)`. Substitute: `2(1) - 3 + 1 = 0`. ✓
