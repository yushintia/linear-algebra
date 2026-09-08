<!-- page break for print -->

## Professor Answer Key (do not hand out this section)

### Part A

**Combo 1:** `det = 3(2) - 1(1) = 6 - 1 = 5`. Nonzero, so exactly one
price exists.

Solve: from `c + 2w = 500`, `c = 500 - 2w`. Substitute into
`3c + w = 1200`: `3(500 - 2w) + w = 1200` → `1500 - 6w + w = 1200` →
`-5w = -300` → `w = 60`. Then `c = 500 - 2(60) = 380`.

**Answer: `c = 380` won, `w = 60` won.** Check: `3(380) + 60 = 1200` ✓,
`380 + 2(60) = 500` ✓.

**Combo 2:** `det = 2(2) - 1(4) = 4 - 4 = 0`. Not exactly one price.
`2200` is not equal to `2 x 1000 = 2000`, so the two equations
contradict each other: **no solution** exists at all.

**Combo 3:** `det = 1(10) - 2(5) = 10 - 10 = 0`. `4500` equals
`5 x 900 = 4500` exactly, so the second equation is just the first
one scaled by 5: **infinitely many solutions** exist (any pair of
prices that satisfies the first equation also satisfies the second).

**Discussion question answer:** Combo 2's determinant is zero and its
constants are *not* proportional the same way, so it has no solution.
Combo 3's determinant is zero and its constants *are* proportional
the same way, so it has infinitely many solutions. A zero determinant
alone cannot tell them apart; the constants must also be checked.

### Part B

**Task 1:**

```
minor for (1,1): [1 -1; 3 1]  ->  det = (1)(1) - (-1)(3) = 1 + 3 = 4
minor for (1,2): [2 -1; 0 1]  ->  det = (2)(1) - (-1)(0) = 2
minor for (1,3): [2  1; 0 3]  ->  det = (2)(3) - (1)(0) = 6
```

```
det = (+1)(4) - (0)(2) + (1)(6) = 4 - 0 + 6 = 10
```

**Determinant: `10`.** Nonzero, so the Iced Mocha recipe has exactly
one exact answer.

**Task 2:**

- **System 1:** `det = 1(4) - 2(3) = -2`. Nonzero. **Invertible.**
- **System 2:** `det = 2(2) - 4(1) = 0`. **Singular.**
- **System 3:** `det = 5(5) - 0(0) = 25`. Nonzero. **Invertible.**

### Part C

**Task 1 (Garden Plot Area):**

`det = 6(4) - 1(2) = 24 - 2 = 22`.

**Area of the parallelogram bed: `22` m².** The diagonal path splits
it into two equal triangles, so the **triangular planting area is
`11` m²** (half of 22).

**Task 2 (Camera-to-Arm Transformation Check):**

**Mount 1:** `det = 2(6) - 3(4) = 12 - 12 = 0`. **Singular.** Row 2
is exactly row 1 scaled by 2, so the transform flattens 2D space onto
a line.

**Mount 2:** `det = 3(4) - 1(2) = 12 - 2 = 10`. Nonzero. **Invertible.**

**Answer:** Mount 1 needs to be recalibrated. Its transform matrix
is singular, so pixel positions cannot be recovered uniquely from
that mount.

**Task 3 (Three-Loop Mesh Determinant):**

```
minor for (1,1): [ 5 -1 ; -1  4 ]  ->  det = (5)(4) - (-1)(-1) = 20 - 1 = 19
minor for (1,2): [-2 -1 ;  0  4 ]  ->  det = (-2)(4) - (-1)(0) = -8 - 0 = -8
minor for (1,3): [-2  5 ;  0 -1 ]  ->  det = (-2)(-1) - (5)(0) = 2 - 0 = 2
```

```
det = (6)(19) - (-2)(-8) + (0)(2) = 114 - 16 + 0 = 98
```

**Determinant: `98`.** Nonzero, so this circuit has exactly one set
of loop currents for any choice of voltage sources.

**Task 4 (Encoding Key Invertibility):**

**Key A:** `det = 3(4) - 5(2) = 12 - 10 = 2`. Nonzero. **Usable:**
the key is invertible, so decoding is always possible.

**Key B:** `det = 4(3) - 6(2) = 12 - 12 = 0`. **Not usable:** the
key is singular. Row 2 is exactly row 1 scaled by 0.5, so different
messages could encode to the same result, and decoding would not be
uniquely reversible.

**Task 5 (Input-Output Model Check):**

**Model 1:** `det = 0.9(0.8) - (-0.2)(-0.3) = 0.72 - 0.06 = 0.66`.
Nonzero. **Invertible:** this model guarantees a unique output
solution for any demand vector.

**Model 2:** `det = 0.6(0.2) - (-0.4)(-0.3) = 0.12 - 0.12 = 0`.
**Singular.**

**Answer:** Relying on Model 2 is risky. A singular coefficient
matrix means the model either has no consistent production plan at
all for some demand targets, or infinitely many equally valid plans
for others, and the determinant alone cannot say which; the economist
would need to check the demand numbers themselves (as in Part A's
Combo 2 vs. Combo 3) before trusting any output figure from it.
