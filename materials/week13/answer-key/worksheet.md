<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1 (guess and check):**

| t | Point | Distance to (4,2) |
|---|---|---|
| 1 | (1,1) | `sqrt((4-1)²+(2-1)²) = sqrt(9+1) = sqrt(10) ≈ 3.16` |
| 3 | (3,3) | `sqrt((4-3)²+(2-3)²) = sqrt(1+1) = sqrt(2) ≈ 1.41` |

The point of Step 1 is that no guess can be *proven* closest by
distance-checking alone against every other point on the line —
only the projection formula, backed by the right-angle rule,
guarantees the closest point.

**Step 2:**

```
y·u = 4(1) + 2(1) = 6
u·u = 1(1) + 1(1) = 2
proj_u(y) = (6/2)(1,1) = 3(1,1) = (3, 3)
```

**Step 3:**

```
z = (4,2) - (3,3) = (1, -1)
```

**Step 4:**

```
z·u = 1(1) + (-1)(1) = 0   ✓
```

**Discussion:** `t = 3` from Step 1 happens to land exactly on
`proj_u(y) = (3,3)`, if students tried it — a coincidence worth
pointing out. In general, guessing cannot confirm closeness the way
the right-angle check does: distance comparison only ranks the
guesses you happened to try, while `z · u = 0` proves no other point
on the line is closer, full stop.

### Part B

**Step 1:**

```
P·Q = 1(0) + 1(0) + 0(2) = 0   ✓ orthogonal, formula applies
```

**Step 2:**

```
y·P = 5(1) + 1(1) + 6(0) = 6
P·P = 1(1) + 1(1) + 0(0) = 2
(y·P)/(P·P) = 6/2 = 3

y·Q = 5(0) + 1(0) + 6(2) = 12
Q·Q = 0(0) + 0(0) + 2(2) = 4
(y·Q)/(Q·Q) = 12/4 = 3

proj_W(y) = 3P + 3Q = (3,3,0) + (0,0,6) = (3, 3, 6)
```

**Step 3:**

```
z = (5,1,6) - (3,3,6) = (2, -2, 0)
```

**Step 4:**

```
z·P = 2(1) + (-2)(1) + 0(0) = 0   ✓
z·Q = 2(0) + (-2)(0) + 0(2) = 0   ✓
```

**Discussion question 1 answer:** The closest drink the machine can
make is `(3, 3, 6)`: equal espresso and milk, double-strength syrup
scaled to 6. The leftover `(2, -2, 0)` tells the barista the customer
usually wants 2 more units of espresso and 2 fewer units of milk than
that closest match — syrup is already exactly right (the leftover's
third coordinate is 0).

**Discussion question 2 answer:**
`(3,3,6) + (2,-2,0) = (5,1,6) = y` ✓. This must always hold because
`z` is *defined* as `y - proj_W(y)`, so adding `proj_W(y)` back in
always reconstructs `y` exactly — this is the orthogonal
decomposition `y = ŷ + z` from the slides, and it holds for any
vector `y` and any subspace `W`, not just this example.

### Part C

**Problem 1 (Computer Graphics — Casting a Shadow):**

```
y · u = 6(1) + 4(0) = 6
u · u = 1(1) + 0(0) = 1
proj_u(y) = (6/1)(1, 0) = (6, 0)
z = (6, 4) - (6, 0) = (0, 4)
z · u = 0(1) + 4(0) = 0   ✓
```

**Question answer:** `proj_u(y) = (6, 0)` is the shadow's position on
the ground (same horizontal position as the object, height 0). `z =
(0, 4)` is exactly the object's height above the ground — the part
"straight down" cannot reach, since the ground line only has room
for the horizontal coordinate.

**Problem 2 (Data Science — The Simplest Possible Model):**

```
y · u = 2 + 4 + 6 = 12
u · u = 1 + 1 + 1 = 3
proj_u(y) = (12/3)(1, 1, 1) = 4(1, 1, 1) = (4, 4, 4)
z = (2, 4, 6) - (4, 4, 4) = (-2, 0, 2)
```

**Question answer:** The plain average is `(2 + 4 + 6)/3 = 4`, exactly
the constant found inside `proj_u(y) = (4, 4, 4)`. This is not a
coincidence: projecting onto the all-ones direction `(1,1,...,1)`
always produces the mean of the data as the best single-number
prediction.

**Problem 3 (Physics — Force Along a Ramp):**

```
F · u = 0(4) + (-50)(3) = -150
u · u = 4² + 3² = 25
proj_u(F) = (-150/25)(4, 3) = -6(4, 3) = (-24, -18)
z = (0, -50) - (-24, -18) = (24, -32)
z · u = 24(4) + (-32)(3) = 96 - 96 = 0   ✓
```

**Question answer:**
```
||proj_u(F)|| = √((-24)² + (-18)²) = √(576 + 324) = √900 = 30 N
||z|| = √(24² + (-32)²) = √(576 + 1024) = √1600 = 40 N
```
Check: `30² + 40² = 900 + 1600 = 2500 = 50²`. Yes — the along-ramp
pull (30 N), the into-ramp push (40 N), and the total weight (50 N)
form a right triangle, exactly as the Pythagorean theorem requires
for two orthogonal components of the same vector.

**Problem 4 (Navigation — Closest Point on a Flight Corridor):**

```
y · u = 10(3) + 5(4) = 30 + 20 = 50
u · u = 3² + 4² = 25
proj_u(y) = (50/25)(3, 4) = 2(3, 4) = (6, 8)
z = (10, 5) - (6, 8) = (4, -3)
z · u = 4(3) + (-3)(4) = 12 - 12 = 0   ✓
```

**Question answer:** The closest point on the corridor is `(6, 8)`
km (east, north). The warehouse is `||z|| = √(4² + (-3)²) = √25 = 5`
km off the corridor.

**Problem 5 (Signal Processing — Approximating with Two Waveforms):**

```
r1 · r2 = 1(1) + 1(-1) + 0(0) = 0   ✓ orthogonal, formula applies

y · r1 = 4(1) + 2(1) + 5(0) = 6
r1 · r1 = 1 + 1 + 0 = 2
(y · r1)/(r1 · r1) = 6/2 = 3

y · r2 = 4(1) + 2(-1) + 5(0) = 2
r2 · r2 = 1 + 1 + 0 = 2
(y · r2)/(r2 · r2) = 2/2 = 1

proj_W(y) = 3 r1 + 1 r2 = (3, 3, 0) + (1, -1, 0) = (4, 2, 0)
z = (4, 2, 5) - (4, 2, 0) = (0, 0, 5)
z · r1 = 0   z · r2 = 0
```

**Question answer:** The third sample (value `5`) is completely
missed. Both reference waveforms have a `0` in the third position, so
no combination of them can ever produce a nonzero third coordinate —
confirmed by `z = (0, 0, 5)`, which isolates exactly that sample and
nothing else.
