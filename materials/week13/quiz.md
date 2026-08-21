# Week 13 Self-Check Quiz

Linear Algebra (501976-001) · Not graded. Answer alone, no notes.
About 10 minutes.

---

**1.** The projection of `y` onto the line spanned by `u` is best
described as:

A. Any point on the line, chosen at random
B. The one point on the line closest to `y`
C. The midpoint between `y` and the origin
D. The length of `u`

**2.** What is `u · u` used for in the projection formula
`proj_u(y) = ((y·u)/(u·u)) u`?

A. It measures the angle between `y` and `u`
B. It is `u`'s squared length, and dividing by it keeps the result pointing along `u`'s direction
C. It is always equal to 1, so it can be ignored
D. It converts `u` into a unit vector before adding it to `y`

**3.** The two-direction projection formula
`proj_W(y) = ((y·u1)/(u1·u1))u1 + ((y·u2)/(u2·u2))u2` is only valid
when:

A. `u1` and `u2` are both unit vectors
B. `y` is already inside the subspace `W`
C. `u1 · u2 = 0`, i.e. `u1` and `u2` are orthogonal
D. `u1` and `u2` have the same length

**4.** The leftover vector `z = y - proj_W(y)` always forms what kind
of angle with the subspace `W`?

A. A right angle (orthogonal)
B. No fixed angle; it depends on `y`
C. A 45-degree angle
D. The same angle as `y` makes with `W`

**5.** In the café case study, the customer's usual drink was
`y = (3, 1, 4)` and the closest drink the machine could make was
`proj_W(y) = (2, 2, 4)`. What was the leftover part `z`?

A. `(2, 2, 4)`
B. `(5, 3, 8)`
C. `(1, -1, 0)`
D. `(0, 0, 0)`

**6.** According to the Best Approximation Theorem, for any point `y`
and subspace `W`, the projection `ŷ`:

A. Is one of several equally close points in `W`
B. Is closer to `y` than every other point in `W`
C. Is only the closest point if `W` is a line, not a larger subspace
D. Equals `y` whenever `y` is not already in `W`

**7.** A student computes a projection and finds the leftover `z`
satisfies `z · u = 3`, not 0. What does this most likely mean?

A. Nothing is wrong; leftovers do not need to be orthogonal to `u`
B. There is an arithmetic error somewhere in the projection calculation
C. `y` must not be a real vector
D. The subspace must have more than one dimension

**8. (Short answer)** Project `y = (6, 2)` onto the line spanned by
`u = (3, 0)`, then find the leftover `z` and verify `z · u = 0`. Show
your steps.

_________________________________________________________________

_________________________________________________________________

---

## Answer Key

1. **B.** The projection is defined as the one point on the line closest to `y`.
2. **B.** `u · u` is `u`'s squared length; dividing by it scales the coefficient without changing `u`'s direction.
3. **C.** The two-direction formula only adds the projections correctly when `u1` and `u2` are orthogonal; otherwise it double-counts part of `y`.
4. **A.** The leftover always forms a right angle with the subspace — that right angle is what proves the projection is the closest point.
5. **C.** `z = y - proj_W(y) = (3,1,4) - (2,2,4) = (1,-1,0)`.
6. **B.** The Best Approximation Theorem guarantees the projection is strictly closer to `y` than every other point in `W`.
7. **B.** A nonzero `z · u` signals a computation mistake; the right angle must hold exactly whenever the projection was computed correctly.
8. `y·u = 6(3)+2(0) = 18`, `u·u = 9+0 = 9`, so `proj_u(y) = (18/9)(3,0) = 2(3,0) = (6,0)`. Leftover: `z = (6,2) - (6,0) = (0,2)`. Check: `z·u = 0(3) + 2(0) = 0` ✓.
