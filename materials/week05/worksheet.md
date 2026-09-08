# Week 5 Worksheet: Factoring the Café's Recipe

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café sells two drinks, Latte and Mocha, from the same two
ingredients: milk and syrup. The recipe amounts never change. Let
`m` = price of 1 unit of milk (won), `s` = price of 1 unit of syrup
(won).

```
Latte: 2m + s = (Latte total)
Mocha: m + 3s = (Mocha total)
```

### Step 1: Write the recipe grid

Fill in the left-side grid of numbers, `A`, from the two recipes
above.

```
A = [       ]
    [       ]
```

### Step 2: Find the multiplier

To zero out the bottom-left entry of `A`, what number do you scale
row 1 by, before subtracting it from row 2?

Multiplier = ______

Compute the new row 2: ______________________________

### Step 3: Write `L` and `U`

```
L = [       ]        U = [       ]
    [       ]            [       ]
```

**Check:** multiply `L` by `U`. Do you get `A` back?

_________________________________________________________________

### Step 4: Solve Monday's receipts

Monday: Latte totaled 800 won, Mocha totaled 900 won.

Forward substitution, solve `Ly = b`:

```
y1 = ______
_____ (y1) + y2 = 900   →   y2 = ______
```

Back substitution, solve `Ux = y`:

```
_____ (x2) = ______   →   x2 = ______ (s)
_____ (x1) + _____ = ______   →   x1 = ______ (m)
```

**Answer:** `m` = ______ won, `s` = ______ won

---

## Part B (about 15 minutes)

### Task 1: Reuse for Tuesday

Tuesday's receipts changed: Latte totaled 700 won, Mocha totaled
1100 won. Reuse the **same** `L` and `U` from Part A. Do not redo
elimination.

```
y1 = ______
_____ (y1) + y2 = 1100   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (s)
_____ (x1) + _____ = ______   →   x1 = ______ (m)
```

**Answer:** `m` = ______ won, `s` = ______ won

### Task 2: Reuse for a new day

A new day's receipts arrive: Latte totaled 1100 won, Mocha totaled
1400 won. Reuse `L` and `U` again.

```
y1 = ______
_____ (y1) + y2 = 1400   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (s)
_____ (x1) + _____ = ______   →   x1 = ______ (m)
```

**Answer:** `m` = ______ won, `s` = ______ won

**Question:** Why didn't you redo elimination for Task 1 or Task 2?

_________________________________________________________________

### Task 3: Does it need pivoting?

For each grid below, decide if a row swap is needed before
elimination can start.

**Grid P**
```
[ 0  3 ]
[ 2  1 ]
```
Needs pivoting? ___________________ Why? __________________________

**Grid Q**
```
[ 5  2 ]
[ 1  4 ]
```
Needs pivoting? ___________________ Why? __________________________

---

## Part C: More Practice (about 25 minutes)

Each task below is a different real-world system. None of them are
the café. Factor once, then reuse `L` and `U` for every extra
right-hand side, exactly as in Parts A and B.

### Task 1: Structural Engineering — Truss Load Distribution

A two-bar support bracket holds up a shelf. Force balance and moment
balance at the two supports give a fixed system relating the two
unknown reaction forces, `F1` and `F2` (kN), to the applied load. The
bracket's geometry never changes; only the applied load does.

```
Load equation 1: 4F1 + 2F2 = (load case total)
Load equation 2: 2F1 + 5F2 = (load case total)
```

**Step 1: Write the grid and factor it.**

```
A = [       ]
    [       ]
```

Multiplier = ______

```
L = [       ]        U = [       ]
    [       ]            [       ]
```

**Step 2: Solve Load Case 1 (bookshelf only).** Totals: 500 kN, 450 kN.

```
y1 = ______
_____ (y1) + y2 = 450   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (F2)
_____ (x1) + _____ = ______   →   x1 = ______ (F1)
```

**Answer:** `F1` = ______ kN, `F2` = ______ kN

**Step 3: Reuse for Load Case 2 (bookshelf + occupancy load).**
Totals: 760 kN, 700 kN. Reuse the same `L` and `U` — do not
refactor.

```
y1 = ______
_____ (y1) + y2 = 700   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (F2)
_____ (x1) + _____ = ______   →   x1 = ______ (F1)
```

**Answer:** `F1` = ______ kN, `F2` = ______ kN

### Task 2: Chemical Mixing — Reactor Batches

A chemical plant blends two raw inputs, Reactant X and Reactant Y,
into two output compounds, Compound P and Compound Q. The reactor's
blending ratios are fixed by its design; only the target batch
amounts change from batch to batch.

```
Compound P: 4x + 2y = (Batch P total, kg)
Compound Q: 2x + 6y = (Batch Q total, kg)
```

**Step 1: Write the grid and factor it.**

```
A = [       ]
    [       ]
```

Multiplier = ______

```
L = [       ]        U = [       ]
    [       ]            [       ]
```

**Step 2: Solve Batch 1.** Totals: Compound P 50 kg, Compound Q 50 kg.

```
y1 = ______
_____ (y1) + y2 = 50   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (y, kg Reactant Y)
_____ (x1) + _____ = ______   →   x1 = ______ (x, kg Reactant X)
```

**Answer:** `x` = ______ kg, `y` = ______ kg

**Step 3: Reuse for Batch 2.** Totals: 76 kg, 78 kg.

```
y1 = ______
_____ (y1) + y2 = 78   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (y)
_____ (x1) + _____ = ______   →   x1 = ______ (x)
```

**Answer:** `x` = ______ kg, `y` = ______ kg

**Step 4: Reuse for Batch 3.** Totals: 100 kg, 100 kg.

```
y1 = ______
_____ (y1) + y2 = 100   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (y)
_____ (x1) + _____ = ______   →   x1 = ______ (x)
```

**Answer:** `x` = ______ kg, `y` = ______ kg

**Question:** Why can the plant reuse the same `L` and `U` for every
batch, no matter how the target amounts change?

_________________________________________________________________

### Task 3: Network Flow — Rush-Hour Traffic

At a small road network, two junctions produce flow-balance
equations relating two unknown road flows, `f1` and `f2`
(vehicles/min). Junction 1's balance only involves Road B; Junction
2's balance involves both roads.

```
Junction 1: 0f1 + 5f2 = (total)
Junction 2: 2f1 + 3f2 = (total)
```

**Step 1: Check pivoting.**

```
[ 0  5 ]
[ 2  3 ]
```

Needs pivoting? ___________________ Why? __________________________

Write the row-swapped grid: ______________________________

**Step 2: Identify `L` and `U`.** Is the swapped grid already upper
triangular? ______ If so, `L` and `U` are:

```
L = [       ]        U = [       ]
    [       ]            [       ]
```

**Step 3: Solve for normal traffic.** Junction 1 total = 300,
Junction 2 total = 260. Remember: when you swap the rows of the
grid, you must also swap the matching rows of `b`.

Swapped `b` = ______

```
y1 = ______
y2 = ______
_____ (x2) = ______   →   x2 = ______ (f2)
_____ (x1) + _____ = ______   →   x1 = ______ (f1)
```

**Answer:** `f1` = ______ veh/min, `f2` = ______ veh/min

**Step 4: Reuse for rush hour.** Junction 1 total = 400, Junction 2
total = 340. Swap `b` the same way, then reuse `L` and `U`.

Swapped `b` = ______

```
y1 = ______
y2 = ______
_____ (x2) = ______   →   x2 = ______ (f2)
_____ (x1) + _____ = ______   →   x1 = ______ (f1)
```

**Answer:** `f1` = ______ veh/min, `f2` = ______ veh/min

### Task 4: Electrical Circuit — Two-Loop Resistor Network

A circuit has two current loops sharing one resistor. Kirchhoff's
Voltage Law gives one equation per loop, relating the loop currents
`I1` and `I2` (mA) to the voltage sources driving each loop. The
resistor values are fixed; only the voltage sources change between
tests.

```
Loop 1: 4I1 - 2I2 = (V1)
Loop 2: -2I1 + 5I2 = (V2)
```

**Step 1: Write the grid and factor it.**

```
A = [       ]
    [       ]
```

Multiplier = ______

```
L = [       ]        U = [       ]
    [       ]            [       ]
```

**Step 2: Solve for Source Set 1.** V1 = 28 V, V2 = 10 V.

```
y1 = ______
_____ (y1) + y2 = 10   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (I2)
_____ (x1) + _____ = ______   →   x1 = ______ (I1)
```

**Answer:** `I1` = ______ mA, `I2` = ______ mA

**Step 3: Reuse for Source Set 2.** V1 = 24 V, V2 = 4 V.

```
y1 = ______
_____ (y1) + y2 = 4   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (I2)
_____ (x1) + _____ = ______   →   x1 = ______ (I1)
```

**Answer:** `I1` = ______ mA, `I2` = ______ mA

**Step 4: Reuse for Source Set 3 (a solar panel is added).** V1 = 40 V,
V2 = 20 V.

```
y1 = ______
_____ (y1) + y2 = 20   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (I2)
_____ (x1) + _____ = ______   →   x1 = ______ (I1)
```

**Answer:** `I1` = ______ mA, `I2` = ______ mA

### Task 5: Manufacturing Cost — Monthly Production Runs

A factory manufactures two products that share two resources, labor
and raw material. The resource-usage grid per production run is
fixed by the factory's process; only the total monthly resource cost
changes. Unknowns: `c` = cost per labor-hour, `d` = cost per unit of
material (both in dollars).

```
Product A run: 5c + 2d = (total cost)
Product B run: 2c + 4d = (total cost)
```

**Step 1: Write the grid and factor it.**

```
A = [       ]
    [       ]
```

Multiplier = ______

```
L = [       ]        U = [       ]
    [       ]            [       ]
```

**Step 2: Solve Run 1.** Totals: 300, 280.

```
y1 = ______
_____ (y1) + y2 = 280   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (d)
_____ (x1) + _____ = ______   →   x1 = ______ (c)
```

**Answer:** `c` = ______ $/hr, `d` = ______ $/unit

**Step 3: Reuse for Run 2.** Totals: 360, 240.

```
y1 = ______
_____ (y1) + y2 = 240   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (d)
_____ (x1) + _____ = ______   →   x1 = ______ (c)
```

**Answer:** `c` = ______ $/hr, `d` = ______ $/unit

**Step 4: Reuse for Run 3.** Totals: 540, 440.

```
y1 = ______
_____ (y1) + y2 = 440   →   y2 = ______
_____ (x2) = ______   →   x2 = ______ (d)
_____ (x1) + _____ = ______   →   x1 = ______ (c)
```

**Answer:** `c` = ______ $/hr, `d` = ______ $/unit
