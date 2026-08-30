<!-- page break for print -->

## Professor Answer Key — do not hand out this section

### Part A

**Step 1:**

```
A = [ 2  1 ]
    [ 1  3 ]
```

**Step 2:** Multiplier `= 1/2 = 0.5`. New row 2: `[1, 3] − 0.5×[2, 1] = [0, 2.5]`.

**Step 3:**

```
L = [ 1    0 ]        U = [ 2   1  ]
    [ 0.5  1 ]            [ 0  2.5 ]
```

Check: `L × U` reproduces `A`. Any equivalent correct verification
(e.g. multiplying row by row) is acceptable.

**Step 4 (Monday, b = 800, 900):**

```
y1 = 800
0.5(800) + y2 = 900   →   y2 = 500
2.5(x2) = 500          →   x2 = 200 (s)
2(x1) + 200 = 800       →   x1 = 300 (m)
```

**Answer: `m = 300` 원, `s = 200` 원.** (Matches the Week 1 answer
key — same recipe, same prices.)

### Part B

**Task 1 (Tuesday, b = 700, 1100):**

```
y1 = 700
0.5(700) + y2 = 1100   →   y2 = 750
2.5(x2) = 750            →   x2 = 300 (s)
2(x1) + 300 = 700         →   x1 = 200 (m)
```

**Answer: `m = 200` 원, `s = 300` 원.**

**Task 2 (new day, b = 1100, 1400):**

```
y1 = 1100
0.5(1100) + y2 = 1400   →   y2 = 850
2.5(x2) = 850             →   x2 = 340 (s)
2(x1) + 340 = 1100         →   x1 = 380 (m)
```

**Answer: `m = 380` 원, `s = 340` 원.**

**Discussion question answer:** The left side of the system, the
recipe grid `A`, never changed — only the right-hand side (the
day's receipts) changed. `L` and `U` depend only on `A`, so they
stay valid for any new right-hand side.

**Task 3:**

- **Grid P: needs pivoting.** The top-left entry is `0`. Elimination
  would try to divide by `0`, so rows 1 and 2 must swap first.
- **Grid Q: does not need pivoting.** The top-left entry is `5`, a
  nonzero number, so elimination can proceed directly.
