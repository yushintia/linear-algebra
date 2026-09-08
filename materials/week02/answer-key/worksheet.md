<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1:**

```
A = [ 2   1 ]      x = [ m ]      b = [ 800 ]
    [ 1   3 ]          [ s ]          [ 900 ]
```

**Step 2:**

- Row 1 (Latte): `2(300) + 1(200) = 800`
- Row 2 (Mocha): `1(300) + 3(200) = 900`

**Step 3:** Yes, `Ax = [800, 900]`, which equals `b` exactly.

**Step 4:** Open discussion. Expected direction: multiplying is
faster to check once you already have candidate numbers; row
reduction is still needed to find the numbers in the first place.

### Part B

**Task 1:**

| `A`'s size | `x`'s entries | Defined? | Answer's size |
|---|---|---|---|
| 3 × 2 | 2 | Yes | 3 |
| 2 × 4 | 3 | No | — |
| 1 × 5 | 5 | Yes | 1 |
| 4 × 4 | 4 | Yes | 4 |

**Task 2:**

```
A = [ 2   1 ]      x = [ m ]      b = [  800 ]
    [ 1   3 ]          [ s ]          [  900 ]
    [ 3   1 ]                         [ 1100 ]
```

**Dimensions:** `A` is now 3 × 2, three rows and two columns. It is
**not** a square matrix (rows ≠ columns), unlike the café's original
3 × 3 recipe matrix from the slides.

**Iced Milk Tea check:** `3(300) + 1(200) = 900 + 200 = 1100`. Yes,
it checks out — this particular extra rule happens to agree with the
same `m` and `s`. Accept answers that correctly compute this and
note the coincidence; do not expect students to generalize about
when a non-square system has a solution, that is Week 3's question.

### Part C

**Task 1:**

```
A = [ 1   1 ]      x = [ i ]      b = [ 5 ]
    [ 2  -1 ]          [ j ]          [ 1 ]
```

- Row 1: `1(2) + 1(3) = 5`
- Row 2: `2(2) - 1(3) = 4 - 3 = 1`

**Yes**, `Ax = [5, 1]`, which equals `b` exactly.

**Task 2:**

```
A = [ 2   1 ]      x = [ w ]      b = [  9 ]
    [ 3   2 ]          [ f ]          [ 16 ]
```

- Small: `2(2) + 1(5) = 4 + 5 = 9`
- Large: `3(2) + 2(5) = 6 + 10 = 16`

Both rows check out with `w = 2`, `f = 5`.

**Task 3:**

```
A = [ 8   6 ]      x = [ w1 ]      b = [ 7.4 ]
    [ 9   7 ]          [ w2 ]          [ 8.4 ]
```

- Athlete 1: `8(0.7) + 6(0.3) = 5.6 + 1.8 = 7.4`
- Athlete 2: `9(0.7) + 7(0.3) = 6.3 + 2.1 = 8.4`

Both rows check out with `w1 = 0.7`, `w2 = 0.3`.

**Task 4:**

| `A`'s size | `x`'s entries | Defined? | Answer's size |
|---|---|---|---|
| 3 × 3 | 3 | Yes | 3 |
| 4 × 2 | 4 | No | — |
| 2 × 3 | 3 | Yes | 2 |
| 5 × 5 | 5 | Yes | 5 |

**Task 5:**

```
A = [ 4   2 ]      x = [ p ]      b = [ 44 ]
    [ 3   5 ]          [ q ]          [ 54 ]
```

- Shipment 1: `4(8) + 2(6) = 32 + 12 = 44`
- Shipment 2: `3(8) + 5(6) = 24 + 30 = 54`

With the third record added:

```
A = [ 4   2 ]      x = [ p ]      b = [ 44 ]
    [ 3   5 ]          [ q ]          [ 54 ]
    [ 2   2 ]                         [ 28 ]
```

**Dimensions:** `A` is now 3 × 2, three rows and two columns. It is
**not** a square matrix.

**Third shipment check:** `2(8) + 2(6) = 16 + 12 = 28`. Yes, it
checks out with the same `p` and `q`.
