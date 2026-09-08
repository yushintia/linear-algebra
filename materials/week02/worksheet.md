# Week 2 Worksheet: The Café, Written as Ax = b

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

Recall Week 1's two drinks. Both are made from **milk** and **syrup**.
You already found the price of each unit by hand:

| Drink | Recipe (per cup) | Total ingredient cost |
|---|---|---|
| Latte | 2 units milk + 1 unit syrup | 800 won |
| Mocha | 1 unit milk + 3 units syrup | 900 won |

Let `m` = price of 1 unit of milk (won), `s` = price of 1 unit of
syrup (won). Week 1 found `m = 300`, `s = 200`.

### Step 1: Write the system as Ax = b

Fill in the coefficient matrix `A`, the unknown vector `x`, and the
known vector `b`:

```
A = [        ]      x = [   ]      b = [    ]
    [        ]          [   ]          [    ]
```

### Step 2: Verify by matrix-vector multiplication

Using `m = 300` and `s = 200`, compute `Ax` row by row (multiply
each row's entries by `x`'s entries, in order, then add):

Row 1 (Latte): ______________________ = ______

Row 2 (Mocha): ______________________ = ______

### Step 3: Compare

Does `Ax` equal `b`? _____________________________________________

### Step 4: Reflect

Week 1 found `m` and `s` by row reduction. This week, you checked the
same answer by multiplying instead. Which felt faster to write down?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Are the sizes compatible?

For each pair below, decide whether `Ax` is defined. If it is, give
the size of the answer (how many entries).

| `A`'s size | `x`'s entries | Defined? | Answer's size (if defined) |
|---|---|---|---|
| 3 × 2 | 2 | | |
| 2 × 4 | 3 | | |
| 1 × 5 | 5 | | |
| 4 × 4 | 4 | | |

### Task 2: A third drink joins the menu

The café adds a third drink, **Iced Milk Tea**: 3 units milk + 1 unit
syrup, priced at 1,100 won, using the same per-unit ingredient costs
as the Latte and Mocha.

Write the **combined** system (all three drinks) as `Ax = b`. `x`
still has only 2 entries (`m` and `s`); there are now 3 rules.

```
A = [        ]      x = [   ]      b = [    ]
    [        ]          [   ]          [    ]
    [        ]                         [    ]
```

**Question:** What are the dimensions of this new `A`? Is it still a
square matrix?

_________________________________________________________________

**Question:** Using `m = 300`, `s = 200`, does the Iced Milk Tea row
also check out? (You do not need to decide whether every possible
system like this has a solution. That question is next week's job.)

_________________________________________________________________

---

## Part C: More Practice (about 25 minutes)

These five problems leave the café behind. Same tools — writing a
system as `Ax = b`, verifying by matrix-vector multiplication, and
checking that sizes are compatible — applied to different real-world
settings.

### Task 1: A circuit's two currents

An electronics workshop measures two unknown currents in a small
circuit board: `i` amps through resistor R1, `j` amps through
resistor R2. Two measurement rules hold:

```
i + j = 5         ... total current entering the junction
2i - j = 1        ... a voltage-loop relationship
```

Write this system as `Ax = b`:

```
A = [        ]      x = [   ]      b = [   ]
    [        ]          [   ]          [   ]
```

Using `i = 2`, `j = 3`, verify by computing `Ax` row by row.

Row 1: ______________________ = ______

Row 2: ______________________ = ______

Does `Ax` equal `b`? _____________________________________________

### Task 2: Scaling a candle recipe

Northside Candle Co. (no relation to the café) sells two candle
sizes, each a blend of soy wax and fragrance oil:

| Candle | Recipe (per candle) | Total ingredient cost |
|---|---|---|
| Small | 2 units wax + 1 unit fragrance oil | 9 dollars |
| Large | 3 units wax + 2 units fragrance oil | 16 dollars |

Let `w` = cost per unit wax, `f` = cost per unit fragrance oil
(dollars).

Write the system as `Ax = b`:

```
A = [        ]      x = [   ]      b = [    ]
    [        ]          [   ]          [    ]
```

Using `w = 2`, `f = 5`, verify both rows check out.

Small: ______________________ = ______

Large: ______________________ = ______

### Task 3: Weighting a gymnastics score

A judging panel scores every routine using two component subscores,
execution (`E`) and difficulty (`D`), combined with two fixed weights
`w1` and `w2` that are the same for every athlete at this meet:

| Athlete | Execution (E) | Difficulty (D) | Final score |
|---|---|---|---|
| Athlete 1 | 8 | 6 | 7.4 |
| Athlete 2 | 9 | 7 | 8.4 |

Write this as `Ax = b`, with `x = (w1, w2)`:

```
A = [        ]      x = [    ]      b = [     ]
    [        ]          [    ]          [     ]
```

Using `w1 = 0.7`, `w2 = 0.3`, verify both rows check out.

Athlete 1: ______________________ = ______

Athlete 2: ______________________ = ______

### Task 4: Are the sizes compatible? (traffic sensor networks)

A city's traffic office models each intersection's sensor network as
`Ax`, where every row of `A` is one intersection's flow equation and
`x` lists the unknown flow rate (cars/minute) on each road segment
being tracked. For each proposed network below, decide whether `Ax`
is defined. If it is, give the size of the answer.

| `A`'s size | `x`'s entries | Defined? | Answer's size (if defined) |
|---|---|---|---|
| 3 × 3 | 3 | | |
| 4 × 2 | 4 | | |
| 2 × 3 | 3 | | |
| 5 × 5 | 5 | | |

### Task 5: A warehouse's shipping weights

A warehouse ships two product types, P and Q, by weight. Two past
shipment records give:

```
4P + 2Q = 44 kg      ... Shipment 1
3P + 5Q = 54 kg      ... Shipment 2
```

Let `p` = weight per unit of P, `q` = weight per unit of Q (kg).
Write as `Ax = b`, then verify using `p = 8`, `q = 6`.

```
A = [        ]      x = [   ]      b = [    ]
    [        ]          [   ]          [    ]
```

Shipment 1: ______________________ = ______

Shipment 2: ______________________ = ______

A third shipment record arrives: `2P + 2Q = 28 kg`. Add it as a new
row to `A` and `b` (`x` still has only 2 entries).

```
A = [        ]      x = [   ]      b = [    ]
    [        ]          [   ]          [    ]
    [        ]                         [    ]
```

**Question:** What are the new dimensions of `A`? Is it a square
matrix?

_________________________________________________________________

**Question:** Using `p = 8`, `q = 6`, does the new shipment row also
check out?

_________________________________________________________________
