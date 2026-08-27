---
marp: true
theme: shintia
paginate: true
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 9: Bases, Dimension

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Ask: "If two ingredients can already make a third, do you
still need to stock all three?" That question is today's hook.
-->

---

<!-- SLOT 2: Where we are (Act 0 / LOCATE) -->

# Where We Are

<div class="roadmap">
<div class="wk"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
<div class="wk"><div class="n">Wk 5</div><div class="t">Factorization</div></div>
<div class="wk"><div class="n">Wk 6</div><div class="t">Determinants</div></div>
<div class="wk"><div class="n">Wk 7</div><div class="t">Vector Spaces · Quiz 1</div></div>
<div class="wk review"><div class="n">Wk 8</div><div class="t">Midterm Exam</div></div>
<div class="wk now"><div class="n">Wk 9</div><div class="t">Bases, Dimension</div></div>
<div class="wk"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: One sentence: last week we described whole spaces; this week we measure and count them. -->

---

<!-- SLOT 3: Recap + open wound (Act 0 / LOCATE) -->

# Last Week, This Week

- **Last week delivered:** we can describe a whole solution space abstractly, using span, null space, and column space
- **Last week left broken:** we still cannot say how "big" that space is, or how many independent directions it needs

<!-- notes: This exact sentence is Week 7's Limit, restated almost verbatim. Week 8 was midterm review, no new pain, so the chain jumps straight from Week 7 to today. -->

---

<!-- SLOT 4: The pain (Act 1 / MOTIVATE), ZERO jargon -->

# Three Flavor Mixes, But How Many Do We Really Need

<div class="pain">

The Campus Café adds a seasonal spice line. Staff test three new
flavor mixes. All three pass every taste rule from last week.

The owner wants a small reference card, listing only the flavor mixes
staff truly need. Any customer request should still be buildable from
that short list.

A staff member notices something odd. Combining two of the mixes
produces something very close to the third mix.

Nobody can tell whether the third mix is genuinely new. It might just
be the other two, combined and relabeled.

</div>

<!-- notes: Do not say "vector," "independent," "basis," or "dimension" yet. Let the "is it really new?" doubt sit before naming anything. -->

---

# More Mixes on the Card, More Wasted Stock

<div class="barchart">
<div class="bar-row">
  <div class="bar-label">1 redundant mix, small kitchen</div>
  <div class="bar-track"><div class="bar-fill short" style="width: 20%"></div></div>
  <div class="bar-value">a little wasted shelf space</div>
</div>
<div class="bar-row">
  <div class="bar-label">3 redundant mixes, busy season</div>
  <div class="bar-track"><div class="bar-fill risk-med" style="width: 60%"></div></div>
  <div class="bar-value">real money tied up, unused</div>
</div>
<div class="bar-row">
  <div class="bar-label">Dozens of mixes, full menu</div>
  <div class="bar-track"><div class="bar-fill long" style="width: 100%"></div></div>
  <div class="bar-value">nobody can tell what is truly needed</div>
</div>
</div>

Without a way to count independent mixes, waste grows with every new
item on the menu.

<!-- notes: Let the widening bars sit for a second before moving on. -->

---

<!-- SLOT 5: Cost of not knowing (Act 1 / MOTIVATE) -->

# What This Actually Costs

- Stocking a redundant mix wastes shelf space and money, every single week
- An engineer who keeps a redundant sensor or control input wastes budget on something that adds no new information
- A data scientist who keeps redundant features slows every model down, without making it any smarter

<div class="why">
<strong>In industry:</strong> "how many independent factors are really
here?" sits behind data compression, sensor design, and machine
learning feature selection. It is a common technical interview
question, often phrased as "how many dimensions does this data need?"
</div>

---

# Same Idea, Many Fields

<div class="appgrid">
<div class="app"><div class="name">Data compression</div><div class="desc">Stores a photo or song using only the independent building blocks, not every duplicate</div></div>
<div class="app"><div class="name">Sensor design</div><div class="desc">Drops a sensor if its readings are just a combination of the others</div></div>
<div class="app"><div class="name">Machine learning</div><div class="desc">Removes redundant features so a model trains faster, without losing information</div></div>
</div>

<!-- notes: One line: same shape as the café's spice mixes, bigger stakes. -->

---

<!-- SLOT 6: Driving question (Act 1 / MOTIVATE) -->

<!-- _class: section -->

# This Week's Question

<div class="driving-q">"How do we find the smallest set of directions that describes a whole space, and count how many we need?"</div>

---

<!-- NEW: Key Words for 차시 1 -->

# Key Words Today

<div class="thread">5 words you will hear all class. Learn them now.</div>

- **Independent (vectors):** none of them can be built by combining the others
- **Redundant (vector):** it can be built by combining the others; it adds nothing new
- **Basis:** the smallest set of independent vectors that still describes an entire space
- **Dimension:** the count of vectors in a basis; how many independent directions a space needs
- **Rank:** the dimension of a matrix's column space

---

<!-- SLOT 7: Learning outcomes (Act 1 / MOTIVATE) -->

# By the End of This Week, You Can

<div class="cardlist">
<div class="card"><div class="h">Independence Test</div><div class="d">Test whether a set of vectors is independent or redundant</div></div>
<div class="card"><div class="h">Find a Basis</div><div class="d">Find a basis for a vector space or subspace</div></div>
<div class="card"><div class="h">Dimension</div><div class="d">State the dimension of a space, and explain why it is one fixed number</div></div>
<div class="card"><div class="h">Rank</div><div class="d">Find the rank of a matrix, and connect it to independent directions</div></div>
</div>

---

<!-- NEW: preview hook, ends 차시 1 -->

# Coming Up: Worksheet Part A

Next session, you test whether a small set of vectors is independent.

You also find a basis for a space, using the café's own flavor mixes.

<div class="why">Bring a pencil. No calculator needed.</div>

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. 차시 2 starts with: who first proved that counting independent directions gives one fixed answer?</div>

---

<!-- NEW: Key Words for 차시 2 -->

# Key Words Today

<div class="thread">4 more words for this session.</div>

- **Linear combination:** a sum of scaled vectors, like `2v + 3w`
- **Trivial combination:** every scalar in a combination is zero
- **Spans (a space):** a set of vectors whose combinations reach every point in that space
- **Exchange lemma:** the rule proving every basis of a space has the same count

---

<!-- SLOT 8: Origin (Act 2 / GROUND) -->

# Counting Directions Is Not New

<div class="thread">You just felt this pain. Others felt it too, over 150 years ago.</div>

- **1844, Germany:** Hermann Grassmann already counts how many "base" directions build every point in a space
- **1913, Germany:** Ernst Steinitz proves that any two such counts, for the same space, always agree

<div class="why">
Before Steinitz, mathematicians worried "dimension" could depend on
which directions you happened to pick. His exchange lemma settled it:
one space, one fixed count, no matter which basis you choose.
</div>

---

# From "How Many?" to One Fixed Answer

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">1844</div><div class="d">Grassmann<br>counts base directions</div></div>
<div class="pt"><div class="dot"></div><div class="y">1888</div><div class="d">Peano<br>vector space rules, formalized</div></div>
<div class="pt"><div class="dot"></div><div class="y">1913</div><div class="d">Steinitz<br>exchange lemma: one fixed count</div></div>
<div class="pt"><div class="dot"></div><div class="y">Today</div><div class="d">Data science<br>"how many dimensions does this data need?"</div></div>
</div>

Dimension only became a trustworthy number once Steinitz proved it
could never change, no matter which basis you pick.

---

<!-- SLOT 9: Core concept (Act 2 / GROUND) -->

# Linear Independence: Definition

<div class="thread">Now the exact, formal definition.</div>

> A set of vectors is **linearly independent** if the only linear
> combination of them that equals the zero vector is the trivial one,
> every scalar equal to zero.
>
> If some other combination also reaches zero, the set is
> **linearly dependent**: at least one vector is redundant, buildable
> from the others.

- Independent means: no vector in the set is hiding inside the others

---

<!-- Act 3 / BUILD -->

# Testing Independence: The Mechanics

<div class="thread">One test covers every case, small or large.</div>

To test vectors `v1, v2, ..., vk`, solve:

```
c1*v1 + c2*v2 + ... + ck*vk = 0
```

- If the **only** solution is `c1 = c2 = ... = ck = 0`, the set is independent
- If some `ci` can be nonzero, the set is dependent. That equation shows how to rebuild the redundant vector

---

# Testing the Café's Three Mixes

<div class="thread">Back to the pain: are all three flavor mixes really new?</div>

The three tested mixes, as ingredient-change vectors `(e, m, s)`:

```
v1 = (-2, 1, 0)
v2 = (1, 0, 1)
v3 = (-1, 1, 1)
```

Try `c1*v1 + c2*v2 + v3 = 0` with `c1 = 1`, `c2 = 1`:

```
1(-2,1,0) + 1(1,0,1) + (-1,1,1)*(-1) = (0,0,0)
```

A nonzero combination reaches zero. The set is dependent.

---

# The Third Mix Was Never New

Rearranging the last slide's equation gives the redundant vector
directly:

```
v3 = v1 + v2
```

Check it: `(-2,1,0) + (1,0,1) = (-1,1,1)`, which is exactly `v3`.

Mixing `v1` and `v2` already produces `v3`. The staff member's hunch
was correct.

---

# Basis: Definition

<div class="thread">Now name the smallest set that still describes everything.</div>

> A **basis** for a space (or subspace) is a set of vectors that is
> both:
>
> 1. Independent — no vector is redundant
> 2. Spanning — every point in the space is some combination of them

A basis is the smallest possible spanning set, and the largest
possible independent set, at the same time.

---

# Finding a Basis: Drop What's Redundant

<div class="thread">A spanning set that is not independent still hides a basis inside it.</div>

To turn `{v1, v2, v3}` into a basis:

1. Keep `v1` and `v2`. They are independent of each other
2. Drop `v3`, since `v3 = v1 + v2` adds no new direction
3. Check `{v1, v2}` still spans every combination `v3` could reach

`{v1, v2}` is a basis for the café's flavor-adjustment space.

---

<!-- SLOT N-2: Worked example -->

# Case Study: The Café's Minimal Recipe Card (1/2)

<div class="thread">This directly answers the pain slide: how many mixes does the card really need?</div>

Every flavor mix that passes the taste rule has the form:

```
m*v1 + s*v2 = m(-2, 1, 0) + s(1, 0, 1)
```

for any numbers `m` and `s`. This is exactly last week's null space,
now written using a basis of just two vectors.

---

# Case Study: Verifying Two Is Enough (2/2)

Any "new" flavor mix a staff member tests is just `m` and `s`
plugged into that formula. Even `v3` fits it:

```
v3 = (-1, 1, 1) = 1*v1 + 1*v2
```

The reference card needs only **2** mixes, `v1` and `v2`. Every valid
flavor mix, past or future, is some combination of those two.

<!-- notes: Point out this directly answers the owner's question from the pain slide: 2 mixes, not 3, and no future test can ever need a 3rd independent one. -->

---

<!-- NEW: Try It, hands off to Worksheet Part A -->

# Try It: Worksheet Part A

<div class="why">Pair up. Open <a href="materials/week09/worksheet.html">Worksheet Part A</a>.</div>

Test a small set of vectors for independence. Then find a basis for a
given space.

You have about 15 minutes.

<!-- notes: Circulate while pairs work. If a pair finishes early, ask them to describe, in words, what a dependent set "wastes." -->

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. 차시 3: turn today's basis into an exact count, dimension.</div>

---

<!-- NEW: Key Words for 차시 3 -->

# Key Words Today

<div class="thread">4 words for the last part of this week.</div>

- **Nullity:** the dimension of a matrix's null space
- **Rank-nullity theorem:** rank plus nullity always equals the number of unknowns
- **Coordinate space:** the space of all lists of n numbers, written Rⁿ
- **Ambient space:** the full space a subspace sits inside, like R³ for the café

---

# Dimension: Definition

<div class="thread">Now the exact, formal definition.</div>

> The **dimension** of a vector space (or subspace) is the number of
> vectors in any basis for it.
>
> Every basis for the same space has the same count. Dimension is
> written `dim(V)`.

- The café's full ingredient space, all `(e, m, s)`, has dimension 3
- The café's flavor-adjustment plane, `span{v1, v2}`, has dimension 2

---

# Every Basis, Same Count

<div class="thread">Why "the" dimension is a safe, single number to trust.</div>

The flavor-adjustment plane also has other valid bases, for example
`{v1, v3}` or `{v2, v3}`.

```
{v1, v2}   -> 2 vectors
{v1, v3}   -> 2 vectors
{v2, v3}   -> 2 vectors
```

Steinitz's exchange lemma guarantees this: pick any basis you like,
you always count exactly 2. Dimension never depends on the choice.

---

# Rank: The Column Space's Dimension

<div class="thread">Week 7 named the column space. This week measures it.</div>

> The **rank** of a matrix `A` is the dimension of its column space:
> how many independent directions `Ax` can actually reach.

- A small rank means many columns of `A` are redundant, combinations of the others
- Rank never exceeds the number of rows or the number of columns, whichever is smaller

---

# Rank-Nullity: All the Directions, Counted

<div class="thread">One theorem ties this week's two counts together.</div>

For any matrix `A` with `n` columns (n unknowns):

```
rank(A) + nullity(A) = n
```

The café's one taste rule is a 1×3 matrix, `A = [2  4  -2]`:

```
rank(A) = 1        nullity(A) = 2        n = 3
1 + 2 = 3   ✓
```

Every ingredient direction is accounted for: 1 constrained, 2 free.

---

<!-- NEW: Try It, hands off to Worksheet Part B -->

# Try It: Worksheet Part B

<div class="why">Same pairs. Open <a href="materials/week09/worksheet.html">Worksheet Part B</a>.</div>

Find the dimension of a small subspace. Then find a matrix's rank, and
check the rank-nullity theorem.

You have about 15 minutes.

---

<!-- SLOT N-1: Common mistakes -->

# Common Mistakes

- **Counting vectors instead of testing them:** more vectors in a set does not mean more dimensions; redundant vectors add nothing
- **Assuming any spanning set is a basis:** a spanning set can still hold a redundant vector; test independence too
- **Forgetting rank-nullity:** rank and nullity always add up to the number of unknowns; use one to check the other

---

<!-- SLOT N: Check yourself -->

# Check Yourself

1. Is the set `{(1, 0), (0, 1), (1, 1)}` linearly independent? Why or why not?
2. A 2×4 matrix has rank 2. What is its nullity?

---

# Answers

1. **No.** `(1, 1) = (1, 0) + (0, 1)`, a nonzero combination reaching a repeat. The set is dependent.
2. **Nullity = 2.** By rank-nullity, `rank + nullity = n = 4`, so `2 + nullity = 4`.

---

<!-- NEW: Try It, hands off to the self-check quiz -->

# Self-Check Quiz

<div class="why">Open the <a href="materials/week09/quiz.html">Week 9 quiz</a>. Answer alone, no notes.</div>

7 short questions, about 10 minutes. This quiz is not graded. It only
shows you what you already know.

---

<!-- SLOT 14: Limits (Act 4 / CLOSE), becomes Week 10 slot 4 -->

# What This Week's Method Cannot Do Yet

<div class="limits">
We can count independent directions, and find the smallest set that
describes any space. But we still cannot find the special directions
a transformation stretches without rotating. Some directions matter
more than others once a matrix acts on a space. Counting alone does
not tell us which ones.
</div>

---

<!-- SLOT 15: Bridge -->

# Next Week

Week 9 leaves one thing unsolved: **finding the special directions a
transformation stretches without rotating.**

**Week 10, Eigenvalues** solves this, starting with Google's own
PageRank problem.

---

<!-- SLOT 16: Summary -->

# Summary

- Independent vectors carry no redundancy; a dependent set always hides at least one vector rebuildable from the rest
- A basis is the smallest independent set that still spans the whole space; every basis has the same size
- Rank is the dimension of a matrix's column space; rank plus nullity always equals the number of unknowns
- **Reading:** Lay, Lay & McDonald, 6th ed., Chapter 4 (sections on basis, dimension, and rank)
- **Handout:** [materials/week09/handout.md](materials/week09/handout.html), glossary and the full café walkthrough
- **Prepare:** review the café's null space from Week 7; bring it to Week 10 for eigenvalues

---

<!-- SLOT 17: Thank You -->
<!-- _class: end -->

# Thank You
