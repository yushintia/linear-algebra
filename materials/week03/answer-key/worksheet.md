<!-- page break for print -->

## Professor Answer Key — do not hand out this section

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
