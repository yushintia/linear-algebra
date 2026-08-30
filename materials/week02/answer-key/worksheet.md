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
