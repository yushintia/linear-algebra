# Week 3 Worksheet: Building and Testing Transformations

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

A new banner design needs the café logo changed by this rule:

> **Rule:** Scale the x-coordinate by 3. Flip the sign of the
> y-coordinate.

### Step 1: Find where the standard basis vectors land

Apply the rule to `(1, 0)` and to `(0, 1)` by hand.

`T(1, 0)` = ( _____ , _____ )

`T(0, 1)` = ( _____ , _____ )

### Step 2: Build the matrix

Each answer above becomes one column. Fill in the matrix:

```
    [ _____  _____ ]
A = [ _____  _____ ]
```

### Step 3: Apply your matrix to two points

Use your matrix from Step 2. Show your work.

Point `(2, 5)`:

_________________________________________________________________

`A(2, 5)` = ( _____ , _____ )

Point `(-1, 4)`:

_________________________________________________________________

`A(-1, 4)` = ( _____ , _____ )

### Step 4: Check

Apply your matrix to `(0, 0)`. What do you get?

_________________________________________________________________

**Question:** Why must this answer always be `(0, 0)`, for any linear
transformation?

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Transform the unit square

The unit square has four corners: `(0,0)`, `(1,0)`, `(0,1)`, `(1,1)`.

Apply this rotation matrix to all four corners:

```
    [ 0  -1 ]
A = [ 1   0 ]
```

| Corner | New position |
|---|---|
| (0, 0) | ( ___ , ___ ) |
| (1, 0) | ( ___ , ___ ) |
| (0, 1) | ( ___ , ___ ) |
| (1, 1) | ( ___ , ___ ) |

Sketch the original square and the new shape on the same grid below
(draw two boxes, one for "before," one for "after"):

```
 before                after



```

### Task 2: Is it a linear transformation?

For each rule, decide **yes** or **no**, and give one reason.

**Rule A:** "Add 2 to every x-coordinate, keep y the same."

Linear transformation? ___________ Reason: ___________________________

**Rule B:** "Multiply every coordinate by -1."

Linear transformation? ___________ Reason: ___________________________

**Rule C:** "Square the x-coordinate, keep y the same."

Linear transformation? ___________ Reason: ___________________________
