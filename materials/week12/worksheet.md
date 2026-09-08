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

## Part C: More Practice (about 25 minutes)

The dot product, length, and angle formulas from Parts A and B are
not just for comparing recipes. The five problems below use the
exact same tools in five different real-world settings.

### Problem 1: Work Done by a Force

A warehouse worker pushes a crate across the floor. Her push is
described by force vector `F = (3, 4)` (in newtons), and the crate
slides along displacement vector `d = (4, 3)` (in meters). In
physics, the work done by a force is exactly a dot product:
`W = F · d`.

```
F · d = ______________________ = ______   (work, in joules)

||F|| = ______________________ = ______

||d|| = ______________________ = ______
```

**Question:** If the worker had instead pushed exactly perpendicular
to the direction the crate slides (`F · d = 0`), how much work would
she do? Does that match your intuition about pushing sideways to the
direction of motion?

_________________________________________________________________

### Problem 2: Surface Lighting

A flat surface in a 3D game has outward-facing normal vector
`n = (0, 0, 1)`. A light source sits in the direction
`L = (0, 3, 4)` from that surface point (all in world units). A
renderer decides how bright to draw the surface by computing the
angle between `n` and `L`. The closer that angle is to 0°, the
brighter the surface.

```
n · L = ______________________ = ______

||n|| = ______

||L|| = ______________________ = ______

cos(angle) = (n · L) / (||n|| · ||L||) = ______

angle ≈ ______
```

**Question:** Is this surface fairly brightly lit, or nearly in
shadow? Explain using your `cos(angle)` value.

_________________________________________________________________

### Problem 3: Crossing Ship Headings

Two ships report velocity vectors in (east, north) knots: Ship A,
`vA = (8, 6)`, and Ship B, `vB = (6, -8)`. A collision-avoidance
officer needs the exact angle between their headings.

```
vA · vB = ______________________ = ______

||vA|| = ______________________ = ______

||vB|| = ______________________ = ______

cos(angle) = ______

angle = ______
```

**Question:** Under navigation right-of-way rules, a "crossing
situation" is when two ships' headings meet at a right angle. Are
these two ships in a crossing situation?

_________________________________________________________________

### Problem 4: Orthogonal Codes

A communications engineer wants to send two signals over the same
channel at the same time, using two 4-sample code vectors:
`s1 = (1, 1, -1, -1)` and `s2 = (1, -1, 1, -1)`. This only works
cleanly if the two codes are orthogonal.

```
s1 · s2 = ______________________ = ______

||s1|| = ______________________ = ______

||s2|| = ______________________ = ______
```

**Question:** Based on your dot product, can the engineer separate
the two signals cleanly later? If `s1 · s2` had come out nonzero
instead, what problem would that create?

_________________________________________________________________

### Problem 5: Comparing Playing Styles

A basketball analytics team tracks each player as a vector of
(points per game, assists per game, rebounds per game). A team's
leading scorer: `X = (20, 5, 5)`. A team's leading playmaker:
`Z = (5, 20, 5)`.

```
X · Z = ______________________ = ______

||X|| = ______________________ = ______

||Z|| = ______________________ = ______

cos(angle) = ______

angle = ______
```

**Question:** Does the angle you found suggest these two players
have very similar roles, very different roles, or something in
between?

_________________________________________________________________
