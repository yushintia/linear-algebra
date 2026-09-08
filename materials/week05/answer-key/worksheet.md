<!-- page break for print -->

## Professor Answer Key (do not hand out this section)

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

**Answer: `m = 300` won, `s = 200` won.** (Matches the Week 1 answer
key — same recipe, same prices.)

### Part B

**Task 1 (Tuesday, b = 700, 1100):**

```
y1 = 700
0.5(700) + y2 = 1100   →   y2 = 750
2.5(x2) = 750            →   x2 = 300 (s)
2(x1) + 300 = 700         →   x1 = 200 (m)
```

**Answer: `m = 200` won, `s = 300` won.**

**Task 2 (new day, b = 1100, 1400):**

```
y1 = 1100
0.5(1100) + y2 = 1400   →   y2 = 850
2.5(x2) = 850             →   x2 = 340 (s)
2(x1) + 340 = 1100         →   x1 = 380 (m)
```

**Answer: `m = 380` won, `s = 340` won.**

**Discussion question answer:** The left side of the system, the
recipe grid `A`, never changed — only the right-hand side (the
day's receipts) changed. `L` and `U` depend only on `A`, so they
stay valid for any new right-hand side.

**Task 3:**

- **Grid P: needs pivoting.** The top-left entry is `0`. Elimination
  would try to divide by `0`, so rows 1 and 2 must swap first.
- **Grid Q: does not need pivoting.** The top-left entry is `5`, a
  nonzero number, so elimination can proceed directly.

### Part C

**Task 1 (Truss Load Distribution):**

```
A = [ 4  2 ]
    [ 2  5 ]
```

Multiplier `= 2/4 = 0.5`. New row 2: `[2, 5] − 0.5×[4, 2] = [0, 4]`.

```
L = [ 1    0 ]        U = [ 4  2 ]
    [ 0.5  1 ]            [ 0  4 ]
```

**Load Case 1 (b = 500, 450):**

```
y1 = 500
0.5(500) + y2 = 450   →   y2 = 200
4(x2) = 200            →   x2 = 50 (F2)
4(x1) + 100 = 500        →   x1 = 100 (F1)
```

**Answer: `F1 = 100` kN, `F2 = 50` kN.**

**Load Case 2 (b = 760, 700), reusing `L`, `U`:**

```
y1 = 760
0.5(760) + y2 = 700   →   y2 = 320
4(x2) = 320             →   x2 = 80 (F2)
4(x1) + 160 = 760         →   x1 = 150 (F1)
```

**Answer: `F1 = 150` kN, `F2 = 80` kN.**

**Task 2 (Reactor Batches):**

```
A = [ 4  2 ]
    [ 2  6 ]
```

Multiplier `= 2/4 = 0.5`. New row 2: `[2, 6] − 0.5×[4, 2] = [0, 5]`.

```
L = [ 1    0 ]        U = [ 4  2 ]
    [ 0.5  1 ]            [ 0  5 ]
```

**Batch 1 (b = 50, 50):**

```
y1 = 50
0.5(50) + y2 = 50   →   y2 = 25
5(x2) = 25            →   x2 = 5 (y)
4(x1) + 10 = 50        →   x1 = 10 (x)
```

**Answer: `x = 10` kg, `y = 5` kg.**

**Batch 2 (b = 76, 78), reusing `L`, `U`:**

```
y1 = 76
0.5(76) + y2 = 78   →   y2 = 40
5(x2) = 40            →   x2 = 8 (y)
4(x1) + 16 = 76        →   x1 = 15 (x)
```

**Answer: `x = 15` kg, `y = 8` kg.**

**Batch 3 (b = 100, 100), reusing `L`, `U`:**

```
y1 = 100
0.5(100) + y2 = 100   →   y2 = 50
5(x2) = 50               →   x2 = 10 (y)
4(x1) + 20 = 100          →   x1 = 20 (x)
```

**Answer: `x = 20` kg, `y = 10` kg.**

**Discussion question answer:** The blending ratio grid `A` is fixed
by the reactor's design. Only the target batch totals (the
right-hand side) change, so the factored `L` and `U` stay valid for
every batch.

**Task 3 (Rush-Hour Traffic):**

The top-left entry of `[0, 5; 2, 3]` is `0`, so pivoting is needed:
rows 1 and 2 must swap. The row-swapped grid is `[2, 3; 0, 5]`,
which is already upper triangular (no elimination step is needed),
so:

```
L = [ 1  0 ]        U = [ 2  3 ]
    [ 0  1 ]            [ 0  5 ]
```

**Normal traffic:** original `b = (300, 260)` (Junction 1, Junction
2). Swapping rows to match the swapped grid gives `b = (260, 300)`.

```
y1 = 260
y2 = 300
5(x2) = 300            →   x2 = 60 (f2)
2(x1) + 180 = 260        →   x1 = 40 (f1)
```

**Answer: `f1 = 40` veh/min, `f2 = 60` veh/min.**

**Rush hour:** original `b = (400, 340)`, swapped `b = (340, 400)`.

```
y1 = 340
y2 = 400
5(x2) = 400            →   x2 = 80 (f2)
2(x1) + 240 = 340        →   x1 = 50 (f1)
```

**Answer: `f1 = 50` veh/min, `f2 = 80` veh/min.**

**Task 4 (Two-Loop Resistor Network):**

```
A = [  4  -2 ]
    [ -2   5 ]
```

Multiplier `= -2/4 = -0.5`. New row 2: `[-2, 5] − (-0.5)×[4, -2] = [0, 4]`.

```
L = [  1    0 ]        U = [ 4  -2 ]
    [ -0.5  1 ]            [ 0   4 ]
```

**Source Set 1 (b = 28, 10):**

```
y1 = 28
-0.5(28) + y2 = 10   →   y2 = 24
4(x2) = 24              →   x2 = 6 (I2)
4(x1) - 12 = 28          →   x1 = 10 (I1)
```

**Answer: `I1 = 10` mA, `I2 = 6` mA.**

**Source Set 2 (b = 24, 4), reusing `L`, `U`:**

```
y1 = 24
-0.5(24) + y2 = 4   →   y2 = 16
4(x2) = 16             →   x2 = 4 (I2)
4(x1) - 8 = 24           →   x1 = 8 (I1)
```

**Answer: `I1 = 8` mA, `I2 = 4` mA.**

**Source Set 3 (b = 40, 20), reusing `L`, `U`:**

```
y1 = 40
-0.5(40) + y2 = 20   →   y2 = 40
4(x2) = 40              →   x2 = 10 (I2)
4(x1) - 20 = 40           →   x1 = 15 (I1)
```

**Answer: `I1 = 15` mA, `I2 = 10` mA.**

**Task 5 (Monthly Production Runs):**

```
A = [ 5  2 ]
    [ 2  4 ]
```

Multiplier `= 2/5 = 0.4`. New row 2: `[2, 4] − 0.4×[5, 2] = [0, 3.2]`.

```
L = [ 1    0 ]        U = [ 5  2   ]
    [ 0.4  1 ]            [ 0  3.2 ]
```

**Run 1 (b = 300, 280):**

```
y1 = 300
0.4(300) + y2 = 280   →   y2 = 160
3.2(x2) = 160           →   x2 = 50 (d)
5(x1) + 100 = 300        →   x1 = 40 (c)
```

**Answer: `c = 40` $/hr, `d = 50` $/unit.**

**Run 2 (b = 360, 240), reusing `L`, `U`:**

```
y1 = 360
0.4(360) + y2 = 240   →   y2 = 96
3.2(x2) = 96             →   x2 = 30 (d)
5(x1) + 60 = 360          →   x1 = 60 (c)
```

**Answer: `c = 60` $/hr, `d = 30` $/unit.**

**Run 3 (b = 540, 440), reusing `L`, `U`:**

```
y1 = 540
0.4(540) + y2 = 440   →   y2 = 224
3.2(x2) = 224            →   x2 = 70 (d)
5(x1) + 140 = 540         →   x1 = 80 (c)
```

**Answer: `c = 80` $/hr, `d = 70` $/unit.**
