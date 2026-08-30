<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Combo 1:** `det = 3(2) - 1(1) = 6 - 1 = 5`. Nonzero, so exactly one
price exists.

Solve: from `c + 2w = 500`, `c = 500 - 2w`. Substitute into
`3c + w = 1200`: `3(500 - 2w) + w = 1200` → `1500 - 6w + w = 1200` →
`-5w = -300` → `w = 60`. Then `c = 500 - 2(60) = 380`.

**Answer: `c = 380` 원, `w = 60` 원.** Check: `3(380) + 60 = 1200` ✓,
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
