# Week 4 Worksheet: Combine and Undo

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

### Task 1: Multiply two matrices

Multiply `A` and `B` below, using the row-by-column rule from class.
Show each entry's calculation.

```
A = [ 2  1 ]      B = [ 1  2 ]
    [ 0  3 ]          [ 1  0 ]
```

`AB` = ______________________________

Top-left entry: ________________________________

Top-right entry: ________________________________

Bottom-left entry: ________________________________

Bottom-right entry: ________________________________

### Task 2: Combine two café price changes

The Campus Café runs a **holiday sale**. Friday prices stay the same
as before: Latte 800 won, Mocha 900 won.

- **Holiday discount `H`:** 15% off the Latte, no change to the Mocha.
- **Member bonus `C`:** adds 5% of the Mocha price onto the Latte
  price (a loyalty rule). The discount applies first, then the bonus.

Write `H` and `C` as matrices:

```
H = [        ]      C = [        ]
    [        ]          [        ]
```

Combine them into one matrix `N = C × H` (discount happens first, so
it goes on the right). Show your work.

_________________________________________________________________

_________________________________________________________________

`N` = ______________________________

Apply `N` to the price vector `p = (800, 900)`. What are the combined
holiday prices?

Latte: ______ won   Mocha: ______ won

### Step 3: Check

Apply `H` to `p` first, then apply `C` to that result. Do you get the
same combined prices as Task 2?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Find an inverse

Find the inverse of `A` below using the 2×2 formula. Show `ad - bc`
first.

```
A = [ 2  1 ]
    [ 1  1 ]
```

`ad - bc` = ______

`A⁻¹` = ______________________________

Check your answer: multiply `A × A⁻¹`. Does it equal `I`?

_________________________________________________________________

### Task 2: Use the inverse to solve a system

Using the **same** `A⁻¹` you just found, solve this system:

```
2p + q = 700
 p + q = 450
```

(Hint: this is `Ax = b` with `b = (700, 450)`. Compute `x = A⁻¹ b`.)

`p` = ______   `q` = ______

### Task 3: Undo a pricing glitch

A register glitch applied `T` below to Friday's prices `(800, 900)`,
producing `(2400, 2700)`.

```
T = [ 3  0 ]
    [ 0  3 ]
```

Find `T⁻¹` and use it to recover the original prices.

`T⁻¹` = ______________________________

Recovered prices: Latte = ______ won   Mocha = ______ won

### Task 4: Classify a matrix

Is the matrix below invertible or singular? Show `ad - bc`.

```
A = [ 4  2 ]
    [ 2  1 ]
```

`ad - bc` = ______

Classification: ___________________

---

## Part C: More Practice (about 25 minutes)

Five more combine-and-undo problems, in five new settings.

### Task 1: A supply chain's tariff and bundling fee

An electronics distributor's unit costs (won) for two components are
`c = (1000, 2000)` (Part X, Part Y). Two rules apply, in this order:

- **Import tariff `D`:** 8% added to Part X's cost, 5% added to
  Part Y's cost.
- **Bundling fee `S`:** adds 10% of Part X's (tariffed) cost onto
  Part Y's cost. Part X is unchanged by this step.

Write `D` and `S` as matrices:

```
D = [        ]      S = [        ]
    [        ]          [        ]
```

Combine them into one matrix `M = S × D` (tariff happens first, so
it goes on the right). Show your work.

_________________________________________________________________

_________________________________________________________________

`M` = ______________________________

Apply `M` to `c = (1000, 2000)`. What are the final costs?

Part X: ______ won   Part Y: ______ won

**Check:** apply `D` to `c` first, then `S` to that result. Do you
get the same answer?

_________________________________________________________________

### Task 2: A simple cipher

A toy cipher (no modular arithmetic, just plain numbers) encodes a
2-number message block `p` by multiplying it by a fixed key matrix:

```
K = [ 3  2 ]
    [ 1  1 ]
```

The message is `p = (4, 7)`. Compute the ciphertext `c = Kp`.

`c` = ( _____ , _____ )

Now find `K⁻¹` using the 2×2 formula, and use it to decode `c` back
into the original message.

`ad - bc` = ______

`K⁻¹` = ______________________________

`K⁻¹ c` = ( _____ , _____ )

Does it match the original `p`? _____________________________________

### Task 3: Is the migration model reversible?

A demographer models one year of migration between a City and its
Suburb with matrix `T`, where `T` applied to this year's population
vector gives next year's:

```
T = [ 0.8  0.4 ]
    [ 0.2  0.1 ]
```

Compute `ad - bc` and classify `T` as invertible or singular.

`ad - bc` = ______

Classification: ___________________

**Question:** If `T` is singular, can the demographer always use
`T⁻¹` to recover last year's populations from this year's? Why or
why not?

_________________________________________________________________

### Task 4: Undoing a scoreboard glitch

An esports tournament's scoreboard software bug tripled every team's
correct point total, applying matrix `G` below. Team Alpha and Team
Beta's correct scores were `(150, 210)`; the bugged scoreboard
displayed `(450, 630)`.

```
G = [ 3  0 ]
    [ 0  3 ]
```

Find `G⁻¹` and use it to recover the correct scores.

`G⁻¹` = ______________________________

Recovered scores: Alpha = ______   Beta = ______

### Task 5: Chaining a robot arm's two moves

A robot arm's controller applies two operations to a tool
coordinate, in this order: first rotate 90° counter-clockwise (`R`),
then scale everything by 2 (`Sc`):

```
R = [ 0  -1 ]      Sc = [ 2  0 ]
    [ 1   0 ]           [ 0  2 ]
```

Combine into one matrix `M = Sc × R` (rotation happens first, so it
goes on the right). Show your work.

_________________________________________________________________

`M` = ______________________________

Apply `M` to the tool coordinate `(3, 1)`.

`M(3, 1)` = ( _____ , _____ )

**Check:** apply `R` to `(3, 1)` first, then `Sc` to that result. Do
you get the same answer?

_________________________________________________________________

**Question:** Is `M` invertible or singular? Show `ad - bc`.

_________________________________________________________________
