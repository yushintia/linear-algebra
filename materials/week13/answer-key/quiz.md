## Answer Key

1. **B.** The projection is defined as the one point on the line closest to `y`.
2. **B.** `u · u` is `u`'s squared length; dividing by it scales the coefficient without changing `u`'s direction.
3. **C.** The two-direction formula only adds the projections correctly when `u1` and `u2` are orthogonal; otherwise it double-counts part of `y`.
4. **A.** The leftover always forms a right angle with the subspace — that right angle is what proves the projection is the closest point.
5. **C.** `z = y - proj_W(y) = (3,1,4) - (2,2,4) = (1,-1,0)`.
6. **B.** The Best Approximation Theorem guarantees the projection is strictly closer to `y` than every other point in `W`.
7. **B.** A nonzero `z · u` signals a computation mistake; the right angle must hold exactly whenever the projection was computed correctly.
8. `y·u = 6(3)+2(0) = 18`, `u·u = 9+0 = 9`, so `proj_u(y) = (18/9)(3,0) = 2(3,0) = (6,0)`. Leftover: `z = (6,2) - (6,0) = (0,2)`. Check: `z·u = 0(3) + 2(0) = 0` ✓.
