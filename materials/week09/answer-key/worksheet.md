<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1:**

- `e`: `-2c1 + c2 = 0`
- `m`: `c1 = 0`
- `s`: `c2 = 0`

From the `m` and `s` equations directly, `c1 = 0` and `c2 = 0`. Only
the trivial combination works, so `{v1, v2}` is **independent**.

**Step 2:** From `v1 + v2 - v3 = 0`: `c1 = 1`, `c2 = 1`, `c3 = -1`.
Since not all are zero, `{v1, v2, v3}` is **dependent**.

**Step 3:** A basis is `{v1, v2}` (circle these two; `v3` is
redundant). Dimension = **2**. Yes, `{v1, v3}` also works as a basis:
it is independent (neither is a multiple of the other) and it spans
the same plane, since `v2 = v3 - v1` is reachable from it. Any two of
the three independent-of-each-other vectors form a valid basis; the
dimension, 2, never changes.

### Part B

**Task 1:** Solve for `e`: `e = 2m - 3s`.

`(e, m, s) = (2m - 3s, m, s) = m(2, 1, 0) + s(-3, 0, 1)`

Basis: `{(2, 1, 0), (-3, 0, 1)}`. Dimension: **2**.

**Task 2:** `rank(A) = 1` (one nonzero row, so its column space is a
single line). `nullity(A) = 2` (matches Task 1). Check:
`rank + nullity = 1 + 2 = 3 = n` (3 unknowns: `e`, `m`, `s`). ✓

**Task 3:**

- **Set 1: independent.** Neither vector is a scalar multiple of the other; only the trivial combination reaches `(0,0)`.
- **Set 2: dependent.** `(4, 2) = 2 · (2, 1)`, so `(4,2)` is redundant.
- **Set 3: dependent.** `(1, 1, 0) + (0, 1, 1) = (1, 2, 1)`, so the third vector is a combination of the first two.

### Part C

**Task 1 (robotics):** `d1 + d2 - d3 = (1+0-1, 0+1-1, 1+1-2) = (0, 0,
0)`, so `c1 = 1`, `c2 = 1`, `c3 = -1` (not all zero). `{d1, d2, d3}`
is **dependent**. Basis: `{d1, d2}` (`d3 = d1 + d2` is redundant).
Dimension: **2** — the arm effectively has only 2 usable degrees of
freedom at this instant, not 3.

**Task 2 (color mixing):** `p3 = 2·p1 + 1·p2`, since
`2(1,0,0) + 1(0,1,0) = (2,1,0)`. Basis: `{p1, p2}`. Dimension: **2**.
No, the rig can never produce a blue-tinted light: every combination
of `p1`, `p2`, `p3` has the form `(x, y, 0)` (the `B`-coordinate is
always 0), so `(0, 0, 1)` is not in `span{p1, p2, p3}`.

**Task 3 (audio):** `w3 = 2·w1 + 3·w2`, since
`2(1,0,-1) + 3(0,1,0) = (2,3,-2)`. Adding `w3` reaches **nothing
new** — it is already a combination of `w1` and `w2`. Dimension of
`span{w1, w2, w3}` = **2**.

**Task 4 (physics):**

- (a) Yes, `f2` is redundant: `f2 = 2·f1` (`(6,8) = 2·(3,4)`).
- (b) Yes, `{f1, f3}` is independent: `f3 = (1,0)` is not a scalar
  multiple of `f1 = (3,4)` (there is no `k` with `3k=1` and `4k=0`
  simultaneously).
- (c) Basis: `{f1, f3}`. Dimension: **2** — since two independent
  vectors already span all of `R²`, `f2` (and any other force in the
  plane) is automatically reachable.

**Task 5 (economics):** `L = 2M - E`.

`(L, M, E) = M(2, 1, 0) + E(-1, 0, 1)`

Basis: `{(2, 1, 0), (-1, 0, 1)}`. Dimension: **2**.

`rank(A) = 1` (one nonzero row). `nullity(A) = 2` (matches the basis
above). Check: `1 + 2 = 3 = n` (3 unknowns: `L`, `M`, `E`). ✓
