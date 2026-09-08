<!-- page break for print -->

## Professor Answer Key (do not hand out this section)

### Part A

**Step 1:**

`T(1, 0) = (3, 0)` (x scaled by 3, y unchanged at 0)

`T(0, 1) = (0, -1)` (x unchanged at 0, y sign flipped)

**Step 2:**

```
    [ 3   0 ]
A = [ 0  -1 ]
```

**Step 3:**

`A(2, 5)`: `x' = 3·2 + 0·5 = 6`, `y' = 0·2 + (-1)·5 = -5`. Result: `(6, -5)`.

`A(-1, 4)`: `x' = 3·(-1) + 0·4 = -3`, `y' = 0·(-1) + (-1)·4 = -4`. Result: `(-3, -4)`.

**Step 4:** `A(0, 0) = (0, 0)`. Every linear transformation must send
the origin to itself; this follows directly from `T(0) = T(0·v) =
0·T(v) = 0`.

### Part B

**Task 1:**

| Corner | New position |
|---|---|
| (0, 0) | (0, 0) |
| (1, 0) | (0, 1) |
| (0, 1) | (-1, 0) |
| (1, 1) | (-1, 1) |

The square rotates a quarter turn counter-clockwise around the origin.
Accept any sketch that shows the square rotated 90 degrees, still the
same size, still touching the origin at one corner.

**Task 2:**

- **Rule A: No.** It moves the origin to `(2, 0)`, not `(0, 0)`. A translation is never a linear transformation.
- **Rule B: Yes.** This is scaling by `-1`; it fixes the origin and is the matrix `[ -1 0 ; 0 -1 ]`, which satisfies both linearity conditions.
- **Rule C: No.** Squaring is not linear: for example, doubling the input x does not double the output x², it quadruples it. `T(2x) ≠ 2·T(x)` in general.

### Part C

**Task 1:**

`T(1, 0) = (3, 0)` (x stretched by 3, y unchanged at 0)

`T(0, 1) = (0, 1/3)` (x unchanged at 0, y squeezed to one-third)

```
    [ 3    0   ]
A = [ 0   1/3  ]
```

`A(3, 6)`: `x' = 3·3 + 0·6 = 9`, `y' = 0·3 + (1/3)·6 = 2`. Result: `(9, 2)`.

`A(-2, 9)`: `x' = 3·(-2) + 0·9 = -6`, `y' = 0·(-2) + (1/3)·9 = 3`. Result: `(-6, 3)`.

**Task 2:**

`T(1, 0) = 1300` won (rate for 1 USD).

`T(0, 1) = 1450` won (rate for 1 EUR).

```
A = [ 1300   1450 ]
```

`A(50, 20) = 1300(50) + 1450(20) = 65000 + 29000 = 94000` won.

**Task 3:**

`A(4, 1)`: row 1: `0(4) + 1(1) = 1`. row 2: `-1(4) + 0(1) = -4`. Result: `(1, -4)`.

**Question:** `A(0, 0) = (0, 0)`, always. Every linear transformation
must fix the origin: `T(0) = T(0·v) = 0·T(v) = 0`, so a sensor
reading of exactly `(0, 0)` always lands at the robot's own origin
in body-frame coordinates too.

**Task 4:**

**Rule D: Yes.** It is pure per-coordinate scaling (matrix
`[ 1.609 0 ; 0 0.3048 ]`); it fixes the origin (`0` miles, `0` feet
maps to `0` km, `0` m) and satisfies both linearity conditions.

**Rule T: No.** `T(0) = (9/5)(0) + 32 = 32 ≠ 0`. A linear
transformation must send `0` to `0`; this rule has a fixed `+32`
offset, so it is only an affine (shifted) rule, not linear.

**Task 5:**

`T(1, 0) = (-1, 0)` (x-component flips sign).

`T(0, 1) = (0, 1)` (y-component unchanged).

```
    [ -1   0 ]
A = [  0   1 ]
```

`A(6, -3)`: `x' = -1(6) + 0(-3) = -6`, `y' = 0(6) + 1(-3) = -3`.
Result: `(-6, -3)`.

**Question:** It must map `(0, 0)` to `(0, 0)`, because every linear
transformation fixes the origin. A ball with zero velocity has
nothing for the bounce to reverse.
