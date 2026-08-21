# Week 9 Handout: Bases, Dimension

Linear Algebra (501976-001) · Dept. of Intelligent Computing

This handout goes with the Week 9 slides. Keep it. You will use the
glossary and the worked example again in later weeks.

---

## 1. Glossary (all key words from this week)

| Word | Plain meaning |
|---|---|
| **Independent (vectors)** | None of them can be built by combining the others. |
| **Redundant (vector)** | It can be built by combining the others; it adds nothing new. |
| **Linear combination** | A sum of scaled vectors, like `2v + 3w`. |
| **Trivial combination** | A linear combination where every scalar is zero. |
| **Linearly independent (set)** | The only combination of the set that equals the zero vector is the trivial one. |
| **Linearly dependent (set)** | Some nonzero combination of the set equals the zero vector; at least one vector is redundant. |
| **Spans (a space)** | A set of vectors whose combinations reach every point in that space. |
| **Basis** | The smallest set of independent vectors that still spans an entire space. |
| **Dimension** | The number of vectors in any basis for a space; the count of independent directions it needs. |
| **Exchange lemma** | The rule proving every basis of the same space has the same count. |
| **Rank** | The dimension of a matrix's column space. |
| **Nullity** | The dimension of a matrix's null space. |
| **Rank-nullity theorem** | Rank plus nullity always equals the number of unknowns (columns) in the matrix. |
| **Coordinate space (Rⁿ)** | The space of all lists of `n` real numbers. |
| **Ambient space** | The full space a subspace sits inside, like R³ around a plane. |

---

## 2. The Café's Minimal Recipe Card, Solved Step by Step

This is the full version of the in-class demo. Read it slowly, one
step at a time.

**The story.** Week 7 found that every recipe adjustment passing the
café's taste rule, `2e + 4m - 2s = 0`, lies in the plane
`span{(-2, 1, 0), (1, 0, 1)}`, a subspace of R³ (the full ingredient
space of espresso `e`, milk `m`, and syrup `s`).

This week, staff test a seasonal spice line and find three flavor
mixes that all pass the rule:

```
v1 = (-2, 1, 0)
v2 = (1, 0, 1)
v3 = (-1, 1, 1)
```

The owner wants the shortest possible reference card. Does the café
really need to track all three?

**Where does the café come from?** The Campus Café is not a real
place — it is a running example invented for this course, and its
numbers are chosen to work out evenly. What is real is the method:
every step below is the general procedure you will use all semester
to test independence and find a basis, following Lay, Lay &
McDonald, 6th ed., Ch. 4.

**Step 1 — Set up the independence test.** Ask whether some nonzero
combination of `v1`, `v2`, `v3` reaches the zero vector:

```
c1*v1 + c2*v2 + c3*v3 = 0
```

**Step 2 — Try a candidate combination.** Try `c1 = 1`, `c2 = 1`,
`c3 = -1`:

```
1(-2, 1, 0) + 1(1, 0, 1) + (-1)(-1, 1, 1)
= (-2 + 1 + 1, 1 + 0 - 1, 0 + 1 - 1)
= (0, 0, 0)
```

**Step 3 — Interpret the result.** A *nonzero* combination
(`c1 = 1`, `c2 = 1`, `c3 = -1` are not all zero) reaches the zero
vector. By definition, `{v1, v2, v3}` is **linearly dependent**.

**Step 4 — Solve for the redundant vector.** Rearrange Step 2:

```
v1 + v2 - v3 = 0
v3 = v1 + v2
```

Check: `(-2, 1, 0) + (1, 0, 1) = (-1, 1, 1)`, exactly `v3`. The third
mix was always just the first two, combined.

**Step 5 — Drop the redundant vector, keep the rest.** `{v1, v2}` is
still independent (neither is a scalar multiple of the other), and it
still spans every combination `v3` could reach, since `v3` is already
inside `span{v1, v2}`.

**Step 6 — Name the result.** `{v1, v2}` is a **basis** for the
flavor-adjustment plane. The plane has **dimension 2**. The reference
card needs exactly 2 mixes, never 3, no matter how many more flavor
mixes staff test in the future — any new one that passes the taste
rule will always be some combination of `v1` and `v2`.

**Step 7 — Check with rank-nullity.** The taste rule is a 1×3 matrix,
`A = [2  4  -2]`. Its column space is a line (rank 1), so its null
space, the flavor-adjustment plane, has:

```
nullity(A) = n - rank(A) = 3 - 1 = 2
```

This matches Step 6 exactly: dimension 2, confirmed two ways.

---

## 3. Optional Reading (not required, not on the quiz)

### 3.1 More history

Hermann Grassmann's 1844 book, already cited in Week 7, went further
than describing spaces: it counted how many "base" directions were
needed to build every point inside one. Grassmann called this count
a space's "Stufenzahl" (roughly, "step number"), an early name for
what we now call dimension.

For decades afterward, mathematicians were not fully sure this count
was trustworthy. Could a clever choice of vectors describe the same
space using fewer, or more, directions than another choice? In 1913,
the German mathematician Ernst Steinitz settled the question with
what is now called the **Steinitz exchange lemma**: given any two
bases for the same finite-dimensional space, you can swap the vectors
of one basis into the other, one at a time, without ever breaking
independence or spanning — and this process always uses up both
bases at exactly the same rate. The conclusion: every basis of a
given space has the *same* number of vectors, no exceptions. Only
after this proof could "the dimension of a space" be called a single,
well-defined number rather than a choice-dependent guess.

Rank has a similarly practical history. Row rank (independent rows)
and column rank (independent columns) were originally studied as
separate ideas by 19th-century algebraists working on systems of
equations. That they are always equal, for any matrix, is itself a
theorem worth knowing exists, even though this course treats it as a
given fact: rank is rank, whether you count by rows or by columns.

### 3.2 Where this shows up in real jobs

- **Data compression:** an image or audio file is stored using only its independent building-block patterns; a "flat" or repetitive region compresses well because it adds few new independent directions.
- **Sensor and control systems:** engineers drop a sensor, or a control input, once its readings are shown to be a combination of the others already installed — this is exactly this week's independence test.
- **Machine learning (dimensionality reduction):** techniques like Principal Component Analysis find the true, lower dimension hiding inside data that looks like it has many more independent features than it actually does.
- **Structural engineering:** the number of independent ways a bridge or frame can flex, its "degrees of freedom," is a dimension count, directly guiding how many supports a design needs.
- **Robotics:** a robot arm's usable range of motion is described by the dimension of the space its joints can reach, which determines how many motors are actually necessary.

None of these show you "a basis" or "a dimension" on the surface. All
of them count one, constantly, underneath.

---

## 4. Practice Problems (with answers)

Try these on your own before checking the answers at the end.

1. Is the set `{(1, 2), (2, 4)}` linearly independent? Why or why not?
2. Is the set `{(1, 0, 0), (0, 1, 0), (0, 0, 1)}` linearly independent? Why or why not?
3. Find a basis for `span{(1, 1), (2, 2), (0, 1)}`, and state its dimension.
4. A 3×5 matrix has rank 3. What is its nullity?
5. A matrix has rank 2 and nullity 2. How many columns (unknowns) does it have?
6. Is `{(1, 0, 0), (0, 1, 0)}` a basis for R³? Why or why not?

### Answers

1. **No.** `(2, 4) = 2 · (1, 2)`, a nonzero combination reaching a repeated direction (`2(1,2) - 1(2,4) = (0,0)`). The set is dependent.
2. **Yes.** No vector here can be built from the other two; only the trivial combination reaches `(0,0,0)`. This is the **standard basis** of R³.
3. `(2, 2) = 2 · (1, 1)`, so it is redundant. `(0, 1)` is not a multiple of `(1, 1)`, so it is genuinely new. A basis is `{(1, 1), (0, 1)}`, and the span has **dimension 2** (all of R²).
4. **Nullity = 2.** By rank-nullity, `rank + nullity = n = 5`, so `3 + nullity = 5`.
5. **4 columns.** `rank + nullity = n`, so `2 + 2 = n = 4`.
6. **No.** It only has 2 vectors, but R³ needs 3 independent directions to span it (its `z`-direction is unreachable). It is a basis for a plane, not for R³.
