# Week 12 Worksheet: How Similar Are Two Recipes?

Linear Algebra (501976-001) · Work with a partner. Bring a pencil.

---

## Part A (about 15 minutes)

The Campus Café adds two more drinks, both made from **milk** and
**syrup**, written as (milk, syrup) vectors.

| Drink | Recipe (per cup) | Vector |
|---|---|---|
| Cappuccino | 3 units milk + 4 units syrup | (3, 4) |
| Flat White | 6 units milk + 8 units syrup | (6, 8) |

Let `u` = Cappuccino's vector, `v` = Flat White's vector.

### Step 1: Dot product

Compute `u · v`. Show your work.

```
u · v =
```

### Step 2: Length of each vector

Find `||u||` and `||v||`. Show your work.

```
||u|| =

||v|| =
```

### Step 3: Distance between the two vectors

Find `||u - v||`. Show your work.

```
u - v =

||u - v|| =
```

**Question:** Flat White uses much more of both ingredients than
Cappuccino. Does that alone tell you whether the two drinks taste
similar? Explain in one sentence.

_________________________________________________________________

---

## Part B (about 15 minutes)

### Task 1: Predict, then compute

**Predict first.** Circle one: Cappuccino and Flat White taste
**more alike** / **more different** / **not sure**.

Now compute the exact angle between `u` and `v` from Part A.

```
cos(angle) = (u · v) / (||u|| · ||v||) =

angle =
```

Was your prediction right? Write one sentence explaining what the
angle tells you that the raw amounts did not.

_________________________________________________________________

### Task 2: Classify each pair

For each pair below, decide: **orthogonal** or **not orthogonal**.
Show the dot product for each.

**Pair 1:** p = (2, 0), q = (0, 3)

```
p · q =
```
Classification: ___________________

**Pair 2:** p = (1, 1), q = (1, 1)

```
p · q =
```
Classification: ___________________

**Pair 3:** p = (2, 3), q = (3, -2)

```
p · q =
```
Classification: ___________________

**Question:** Pair 3 is not made of simple axis vectors like Pair 1.
How did you tell it was orthogonal without drawing a picture?

_________________________________________________________________

---

<!-- page break for print -->

## Instructor Answer Key — do not hand out this section

### Part A

**Step 1 (dot product):**

```
u · v = (3)(6) + (4)(8) = 18 + 32 = 50
```

**Step 2 (length):**

```
||u|| = √(3² + 4²) = √(9 + 16) = √25 = 5
||v|| = √(6² + 8²) = √(36 + 64) = √100 = 10
```

**Step 3 (distance):**

```
u - v = (3 - 6, 4 - 8) = (-3, -4)
||u - v|| = √((-3)² + (-4)²) = √(9 + 16) = √25 = 5
```

**Discussion answer:** No. Flat White is a bigger batch, but bigger
amounts alone do not say whether the *ratio* of milk to syrup is the
same or different. Size and direction are separate questions.

### Part B

**Task 1:**

```
cos(angle) = 50 / (5 · 10) = 50 / 50 = 1
angle = 0°
```

Any reasonable prediction is acceptable; the point is the check.
Accept any answer noting that an angle of 0° means the two recipes
point in exactly the same direction: Flat White is just Cappuccino,
doubled. The raw amounts looked very different, but the flavor ratio
is identical.

**Task 2 classification:**

- **Pair 1: orthogonal.** `p · q = (2)(0) + (0)(3) = 0`.
- **Pair 2: not orthogonal.** `p · q = (1)(1) + (1)(1) = 2`.
- **Pair 3: orthogonal.** `p · q = (2)(3) + (3)(-2) = 6 - 6 = 0`.

**Discussion question answer:** Compute the dot product algebraically
and check whether it equals zero. This works in any number of
dimensions, even when a picture is not possible.
