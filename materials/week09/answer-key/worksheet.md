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
