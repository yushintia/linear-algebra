---
marp: true
theme: shintia
paginate: true
math: katex
footer: 'Department of Intelligent Computing'
---

<!-- SLOT 1: Title -->
<!-- _class: title -->

# Week 1: Introduction

<span class="subtitle">Linear Algebra (501976-001)</span>

<div class="meta">
Yushintia Pramitarini, Ph.D · Dept. of Intelligent Computing · Tue [1-3] · 정보 610
</div>

<!--
notes: Welcome the class. This session is the course contract: what this
course covers, how it's graded, what's expected of you, and how the
semester runs. No equations yet - that starts next week.
-->

---

<!-- SLOT 2: Where we are -->

# Where We Are

<div class="roadmap">
<div class="wk now"><div class="n">Wk 1</div><div class="t">Linear Systems</div></div>
<div class="wk"><div class="n">Wk 2</div><div class="t">Vector &amp; Matrix</div></div>
<div class="wk"><div class="n">Wk 3</div><div class="t">Linear Transformation</div></div>
<div class="wk"><div class="n">Wk 4</div><div class="t">Matrix Algebra</div></div>
<div class="wk"><div class="n">Wk 5</div><div class="t">Factorization</div></div>
<div class="wk"><div class="n">Wk 6</div><div class="t">Determinants</div></div>
<div class="wk"><div class="n">Wk 7</div><div class="t">Vector Spaces · Quiz 1</div></div>
<div class="wk review"><div class="n">Wk 8</div><div class="t">Midterm Exam</div></div>
<div class="wk"><div class="n">Wk 9</div><div class="t">Bases, Dimension</div></div>
<div class="wk"><div class="n">Wk 10</div><div class="t">Eigenvalues</div></div>
<div class="wk"><div class="n">Wk 11</div><div class="t">Diagonalization</div></div>
<div class="wk"><div class="n">Wk 12</div><div class="t">Orthogonality</div></div>
<div class="wk"><div class="n">Wk 13</div><div class="t">Projections</div></div>
<div class="wk"><div class="n">Wk 14</div><div class="t">Least Squares · Quiz 2</div></div>
<div class="wk review"><div class="n">Wk 15</div><div class="t">Final Exam</div></div>
</div>

<!-- notes: Point at the row. Say: "Fifteen weeks, one growing toolkit. Today is the odd one out - it's about how this course works, not a technique. Weeks 8 and 15 are exams; the other twelve each add one new piece of the toolkit." -->

---

<!-- Course intro: why this course, briefly, before the contract -->

# Why This Course

<div class="thread">One shared problem, everywhere you look.</div>

Every technique this semester solves the same kind of problem: several
unknown amounts, several known facts about them, and one exact answer
- found without guessing.

Linear algebra sits behind GPS positioning, computer graphics,
economic models, and nearly every machine learning method you will
meet later in this major. It is also a common topic in technical
interviews and in later courses that assume you already know it.

---

# Where Linear Algebra Shows Up

<div class="thread">The same toolkit, reused across very different fields.</div>

<div class="appgrid">
<div class="app"><div class="name">GPS &amp; Navigation</div><div class="desc">pinpoints your location from several satellite signals at once</div></div>
<div class="app"><div class="name">Computer Graphics</div><div class="desc">moves, resizes, and rotates every object on screen</div></div>
<div class="app"><div class="name">Machine Learning</div><div class="desc">stores and updates millions of numbers as one linked object</div></div>
<div class="app"><div class="name">Economics</div><div class="desc">models many interacting markets as one linked system</div></div>
<div class="app"><div class="name">Search &amp; Recommendations</div><div class="desc">ranks pages and products from linked ratings data</div></div>
<div class="app"><div class="name">Engineering</div><div class="desc">solves the same-shaped system for every design test</div></div>
</div>

---

# Meet the Campus Café

<div class="thread">Not software you build. A story every worked example borrows from.</div>

Throughout the semester, examples are drawn from the **Campus Café**:
a made-up café whose drink recipes give every technique a concrete,
familiar shape.

The café's drink uses three ingredients: espresso, milk, and syrup.
Every example this term starts from this same small recipe, so the
numbers stay familiar even as the technique changes.

<!-- notes: The Campus Café is invented; the numbers come later. Today,
just introduce the setting. -->

---

# The Café's New Problem

A regular customer asks for a new version: the same drink, plus a
fourth ingredient, vanilla syrup. Simple multiplication does not help
- there is no old vanilla amount to scale up, and the original three
amounts were never exact either.

This is the shape of problem this course solves: several unknowns,
several known facts, found exactly - not by guessing.

<!-- notes: Let the class sit with the shape of the problem. -->

---

# A Question for Later

<div class="thread">One question, then straight into the course contract.</div>

If doubling a recipe is not just "multiply by 2" once a new
ingredient joins it, how do you find the right amounts?

- Could you find them by trial and error alone?
- Would two people, each guessing carefully, land on the same answer?

<!--
notes: A discussion prompt, not a lesson - do not answer it today.
Just let the class sit with the question for a moment. A later week
opens with exactly this scenario and answers it properly.
-->

---

<!-- SLOT 6: Driving question -->

<!-- _class: section -->

# This Course's Question

<div class="driving-q">"How do we find exact answers when there are several unknowns and several facts about them, without guessing?"</div>

---

# This Course's Four Goals

<div class="thread">Not just today's goal. This is the whole course, in four lines.</div>

| # | Goal (from the syllabus) | Where |
|---|---|---|
| 1 | Solve linear systems; find matrix inverses and factorizations | Weeks 1-2, 4-5 |
| 2 | Compute and use determinants | Week 6 |
| 3 | Find vector space properties, bases, and dimension | Weeks 7, 9 |
| 4 | Compute eigenvalues and diagonalize matrices | Weeks 10-11 |

Weeks 12-14 combine all four goals: fitting a line to real, noisy
data, the final payoff of this course.

---

# Goal 1: Solve, Invert, Factor

<div class="thread">The foundation everything else builds on.</div>

Weeks 1-2 and 4-5 build the core toolkit: write a system compactly,
combine and reverse the changes a matrix makes, and factor a matrix
so a large system solves fast, not from scratch every time.

<div class="why">This goal alone covers roughly a third of the semester - it is the base every later goal depends on.</div>

---

# Goal 2: Determinants

<div class="thread">One number, one sharp yes-or-no answer.</div>

Week 6 gives you a single number, computed from a matrix, that tells
you whether a system has a unique solution before you even try to
solve it.

This closes a gap every earlier week leaves open: knowing *whether*
a solution exists, not just how to look for one.

---

# Goal 3: Vector Spaces, Bases, Dimension

<div class="thread">Describing the whole space of possible answers, not just one.</div>

Weeks 7 and 9 move past single solutions to describe an entire space
of them at once: what counts as an independent direction, and how
many independent directions a system actually has.

<div class="why">Quiz 1, in Week 7, checks the first half of the semester's toolkit.</div>

---

# Goal 4: Eigenvalues & Diagonalization

<div class="thread">Finding the directions a transformation stretches, and repeating it fast.</div>

Weeks 10-11 find the special directions a matrix stretches without
rotating, then use them to make repeating a transformation many
times fast instead of slow.

This is the last new mechanical tool before the semester turns to
measuring and approximating, in Weeks 12-14.

---

<!-- _class: section -->

# End of 차시 1
<div class="driving-q">Short break. Next: the course contract - what's covered, how you're graded, and what's expected of you.</div>

---

# Course Description

<div class="thread">From the official syllabus.</div>

This course introduces the fundamentals of linear algebra: systems of
linear equations, vectors and matrices, linear transformations, matrix
algebra and factorization, determinants, vector spaces, eigenvalues,
orthogonality, and least-squares approximation. Throughout, the
emphasis is on solving problems exactly, not by guesswork, with
applications in computer graphics, data science, and machine learning.

---

# Topics Covered at a Glance

<div class="thread">The same list, as one-word tags instead of one paragraph.</div>

<div class="chip-row">
<span class="chip">Linear Systems</span>
<span class="chip">Vectors</span>
<span class="chip">Matrices</span>
<span class="chip">Transformations</span>
<span class="chip">Matrix Algebra</span>
<span class="chip">Factorization</span>
<span class="chip">Determinants</span>
<span class="chip">Vector Spaces</span>
<span class="chip">Eigenvalues</span>
<span class="chip">Orthogonality</span>
<span class="chip">Least Squares</span>
</div>

Eleven topics, fifteen weeks, one running example tying them together.

---

# Learning Objectives (Part 1)

<div class="thread">The official course objectives, from the syllabus - what you'll be able to do by Week 15.</div>

By the end of this course, you can:

<div class="cardlist">
<div class="card"><div class="h">Row Reduction</div><div class="d">Solve systems of linear equations exactly, using row reduction.</div></div>
<div class="card"><div class="h">Vectors &amp; Matrices</div><div class="d">Represent linear systems and transformations using vectors and matrices.</div></div>
<div class="card"><div class="h">Matrix Operations</div><div class="d">Compute matrix operations: multiplication, inverses, and factorizations.</div></div>
<div class="card"><div class="h">Determinants</div><div class="d">Compute and interpret determinants.</div></div>
</div>

---

# Learning Objectives (Part 2)

<div class="thread">The rest of the list - continued from the previous slide.</div>

<div class="cardlist">
<div class="card"><div class="h">Vector Spaces</div><div class="d">Describe vector spaces, bases, and dimension.</div></div>
<div class="card"><div class="h">Eigenvalues &amp; Diagonalization</div><div class="d">Compute eigenvalues and eigenvectors, and diagonalize matrices.</div></div>
<div class="card"><div class="h">Orthogonality &amp; Least Squares</div><div class="d">Apply orthogonality and least-squares methods to fit real, noisy data.</div></div>
</div>

Seven objectives, matched one-to-one with the eleven topics on the
previous slides.

---

# Prerequisites: The Short Answer

<div class="thread">What this course assumes you already have.</div>

No formal prerequisite is required for this course. But you already
know useful things:

- High school algebra
- Programming, if you've taken it
- Basic arithmetic

The next three slides take each of these in turn.

---

# Prerequisite: High School Algebra

You have solved two equations with two unknowns before, even if you
never called it "linear algebra."

<div class="why">This course does not introduce that idea. It gives it an exact method that still works when there are ten unknowns, not just two.</div>

---

# Prerequisite: Programming Experience

If you've taken a programming course, you already think in variables
and operations on them.

This course makes that habit formal: a vector or a matrix is just a
variable that happens to hold many numbers at once, with its own
rules for combining them.

---

# Prerequisite: Basic Arithmetic

Fractions and negative numbers are the only math skill this course
strictly assumes.

This course does not teach new arithmetic. It teaches an exact way to
solve many equations at once, without guessing.

---

# Textbooks: Primary

<div class="thread">One primary text. Everything else is optional support.</div>

**Primary:** Lay, Lay & McDonald, *Linear Algebra and Its
Applications*, 6th ed., Pearson, 2020. Every week's reading points
here - buy or borrow this one first.

---

# Textbooks: References

<div class="thread">Optional, if the primary text's explanation doesn't click.</div>

- Hefferon, *Linear Algebra*, 4th ed. (open textbook, free online)
- Cherney, Denton, Thomas & Waldron, *Linear Algebra*, UC Davis, 2013
  (also free online)

Neither reference is required reading. Use them only if you want a
second explanation of the same week's topic.

---

# These Slides as a Reference

These lecture slides themselves are a listed course reference. Every
week's deck includes a handout with a glossary and the full worked
example, linked from that week's Summary slide.

Slides, handout, and the primary textbook together cover everything
graded in this course.

---

# How This Course Runs

<div class="thread">What to expect from a 3×50-minute block, every week.</div>

Each session mixes short lecture with four recurring pieces. The next
four slides walk through each one.

---

# Format: A Warm-Up

A short, concrete question opens every session, before any jargon.

The goal is to get you thinking about the week's problem in plain
language, the same way the Campus Café's problems are introduced.

---

# Format: A Recap

Every session after the first opens with what last week delivered,
and what it left unsolved.

This is deliberate: the whole semester is one argument, not fifteen
separate topics, and the recap is the thread that ties them together.

---

# Format: Pair Activities

You solve a piece of that week's running example with a partner,
worksheet in hand, and the answer is discussed right after.

Pair work catches mistakes faster than working alone, and it means
you talk through the reasoning, not just the arithmetic.

---

# Format: A Self-Check Quiz

Each week ends with a short, ungraded quiz - just for you, to show
what you already know before the next session builds on it.

You will talk in this class, not just listen.

---

# Weekly Schedule: Weeks 1-8

<div class="thread">The first half of the semester, one line per week.</div>

| Wk | Topic |
|---|---|
| 1 | Introduction (today) |
| 2 | Vector & Matrix |
| 3 | Linear Transformation |
| 4 | Matrix Algebra - **Assignment 1** |
| 5 | Factorization |
| 6 | Determinants |
| 7 | Vector Spaces - **Quiz 1** |
| 8 | **Midterm Exam** (Wks 1-7) |

---

# Weekly Schedule: Weeks 9-15

<div class="thread">The second half of the semester, same format.</div>

| Wk | Topic |
|---|---|
| 9 | Bases, Dimension |
| 10 | Eigenvalues |
| 11 | Diagonalization - **Assignment 2** |
| 12 | Orthogonality |
| 13 | Projections |
| 14 | Least Squares - **Quiz 2** |
| 15 | **Final Exam** (Wks 9-14) |

---

# Assignment & Quiz Checkpoints

<div class="thread">The graded dates from both schedules, gathered in one place.</div>

<div class="timeline">
<div class="pt"><div class="dot"></div><div class="y">Wk 4</div><div class="d">Assignment 1<br>due</div></div>
<div class="pt"><div class="dot"></div><div class="y">Wk 7</div><div class="d">Quiz 1</div></div>
<div class="pt"><div class="dot"></div><div class="y">Wk 8</div><div class="d">Midterm Exam</div></div>
<div class="pt"><div class="dot"></div><div class="y">Wk 11</div><div class="d">Assignment 2<br>due</div></div>
<div class="pt"><div class="dot"></div><div class="y">Wk 14</div><div class="d">Quiz 2</div></div>
<div class="pt"><div class="dot"></div><div class="y">Wk 15</div><div class="d">Final Exam</div></div>
</div>

Six dates, spread across fifteen weeks. Mark them now.

---

<!-- _class: section -->

# End of 차시 2
<div class="driving-q">Short break. Next: grading, assignments, and policy.</div>

---

<!-- Course logistics: grading, assignments, and policy (outside spine numbering) -->

# Grading

<div class="thread">Five components, 100% total.</div>

| Component | Weight |
|---|---|
| Attendance | 10% |
| Midterm | 30% |
| Final | 30% |
| Assignments (×2) | 10% |
| In-class items | 20% |

<!-- notes: Assignment 1 due Week 4. Assignment 2 due Week 11. Quiz 1 Week 7. Quiz 2 Week 14. -->

---

# Grade Distribution Guideline

<div class="why">
<strong>Grade distribution guideline:</strong> A ≤30%, B ≤40%, C-F ≤30%
of the class. This may shift after the add/drop period, based on final
enrollment.
</div>

This is a guideline, not a hard curve fixed on day one - it can move
once final enrollment settles.

---

# Grading Detail: Assignments (10%)

The 10% assignments weight splits across the two graded assignments
in the Weekly Schedule: Assignment 1 (Week 4) and Assignment 2 (Week
11), each worth 5% of your final grade.

---

# Grading Detail: In-Class Items (20%)

The 20% in-class items weight covers the pair-activity worksheets and
self-check quizzes described in "How This Course Runs" - completed in
class, not take-home work.

<div class="why">Quiz 1 and Quiz 2 are graded separately and are not part of this 20%; see the Weekly Schedule.</div>

---

# Grading Detail: Midterm & Final (60%)

Together, the midterm and final make up 60% of your grade - the
single largest share. The midterm (Week 8) covers Weeks 1-7; the final
(Week 15) covers Weeks 9-14.

---

# Assignments

<div class="thread">Two assignments, spaced across the semester.</div>

| # | Released | Due | Topics |
|---|---|---|---|
| 1 | Wk 2 | Wk 4 | Linear systems, vectors, matrices, matrix algebra |
| 2 | Wk 9 | Wk 11 | Bases, dimension, eigenvalues, diagonalization |

---

# Assignment 1 in Detail

Released Week 2, due Week 4. Covers linear systems, vectors, matrices,
and matrix algebra - everything taught in Weeks 1 through 4.

By the time it's due, you will have seen every technique it asks you
to use, worked through in class first.

---

# Assignment 2 in Detail

Released Week 9, due Week 11. Covers bases, dimension, eigenvalues,
and diagonalization - the material from Weeks 9 through 11.

Like Assignment 1, nothing on it is untaught: it checks material
already covered in class by its due date.

---

# Feedback Policy

<div class="thread">From the syllabus, verbatim.</div>

> Assignments graded within one week with rubric and model answers;
> exam item-analysis shared with weak-topic guidance and individual
> review on request.

In plain terms: you will know what you got wrong, and why, quickly
enough for it to still matter for the next assignment or exam.

---

# What Feedback Looks Like

<div class="thread">Concretely, not just in policy language.</div>

For Assignment 1, due Week 4, expect graded work back with a rubric
and model answers by Week 5 - in time to apply the feedback before
Assignment 2 opens in Week 9.

For the midterm, expect an item-by-item breakdown of which topics the
class struggled with, plus an offer of individual review.

---

# Attendance Policy

<div class="thread">Concrete rules, stated once, so nobody is surprised later.</div>

Attendance is 10% of your grade and is recorded every session.

---

# Late Arrival Policy

Arriving within 15 minutes of the start is on-time; after that, you're
marked late. Three lates equal one absence.

---

# Can't Attend?

Email the professor *before* the session to be marked excused -
unexcused absences aren't eligible for makeup credit.

---

# Late Work Policy

Late work loses 10% of that assignment's grade per day late, up to 3
days. No credit after 3 days, unless arranged with the professor in
advance.

---

# Academic Integrity: What Counts as a Violation

<div class="thread">Same principle as attendance: stated once, plainly.</div>

Submit your own work. Copying another student's work, having someone
else complete it for you, or submitting unattributed AI-generated
work as your own is a violation.

---

# Academic Integrity: Consequences

**First violation:** zero credit on that assignment or exam, plus a
formal report. **Repeat violation:** may result in failing the
course, per university policy.

If anything here is unclear, ask - now is the cheapest time to ask.

---

# Accommodations: Hearing-Impaired

<div class="thread">From the syllabus's accommodations section.</div>

Front-row seating, lecture material files provided where possible,
urgent notices given in writing.

---

# Accommodations: Mobility-Impaired

Extended exam time.

---

# Accommodations: Other Documented Conditions

Extended exam time, materials provided in advance, enlarged exam
copies, or other reasonable accommodation based on need.

---

# How to Request Accommodations

Contact the professor early, and the Disability Student Support
Center or Academic Affairs Team, so accommodations are ready before
you need them.

---

# Contact

<div class="thread">How to reach the professor.</div>

- **Email:** yushintia@deu.ac.kr
- **Office hours:** by email appointment
- Email is the fastest way to reach the professor outside of class.

---

# Getting the Most from Office Hours

<div class="thread">A practical tip, not a new rule.</div>

Email ahead with the specific question or topic you want to cover.
An office-hours slot spent reviewing a targeted question goes further
than a general "I don't understand this week."

---

<!-- SLOT N+1: Limits (Act 4 / CLOSE), reused as Week 2's slot 3 recap gap -->

# What Today Doesn't Give You Yet

<div class="limits">
You now know how this course runs, how you're graded, and what's
expected of you. You still do not have a way to find the café's
fourth ingredient amount - or any set of unknowns - without guessing.
Knowing the rules of the course is not the same as knowing how to
solve for unknowns when the numbers get complicated.
</div>

---

<!-- SLOT N+2: Bridge -->

# Next Week

Week 1 leaves one thing unsolved: **how to find unknown amounts, like
the café's fourth ingredient, without guessing.** **Week 2, Vector and
Matrix**, begins building the tools for this: a compact way to write
down many linked unknowns at once.

---

<!-- SLOT N+3: Summary -->

# Summary

- This course: solving linear systems exactly, representing and
  transforming them with matrices, and applying that toolkit to real,
  noisy data - grounded in one running example, the Campus Café.
- Grading: Attendance 10%, Midterm 30%, Final 30%, Assignments 10%,
  In-class items 20%.
- Assignments due Weeks 4 and 11. Graded within one week, with a
  rubric and model answers.
- Primary text: Lay, Lay & McDonald, 6th ed. Contact: yushintia@deu.ac.kr.
- **Prepare:** skim Chapter 1 before Week 2. No exercises due.

---

<!-- SLOT N+4: Thank You -->
<!-- _class: end -->

# Thank You
