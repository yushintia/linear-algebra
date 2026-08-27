---
marp: true
theme: shintia
paginate: true
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

# This Semester's Running Example

<div class="thread">Not software you build. A story every worked example borrows from.</div>

Throughout the semester, examples are drawn from the **Campus Café**:
a made-up café whose drink recipes give every technique a concrete,
familiar shape.

The café's drink uses three ingredients: espresso, milk, and syrup. A
regular customer asks for a new version: the same drink, plus a
fourth ingredient, vanilla syrup. Simple multiplication does not help
- there is no old vanilla amount to scale up, and the original three
amounts were never exact either.

This is the shape of problem this course solves: several unknowns,
several known facts, found exactly - not by guessing.

<!-- notes: The Campus Café is invented; the numbers come later. Today,
just let the class sit with the shape of the problem. -->

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

# Learning Objectives

<div class="thread">The official course objectives, from the syllabus - what you'll be able to do by Week 15.</div>

By the end of this course, you can:

1. Solve systems of linear equations exactly, using row reduction.
2. Represent linear systems and transformations using vectors and matrices.
3. Compute matrix operations: multiplication, inverses, and factorizations.
4. Compute and interpret determinants.
5. Describe vector spaces, bases, and dimension.
6. Compute eigenvalues and eigenvectors, and diagonalize matrices.
7. Apply orthogonality and least-squares methods to fit real, noisy data.

---

# Prerequisites

<div class="thread">What this course assumes you already have.</div>

No formal prerequisite is required for this course. But you already
know useful things:

- **High school algebra:** you have solved two equations with two unknowns before
- **Programming, if you've taken it:** you already think in variables and operations; this course makes that idea formal
- **Basic arithmetic:** fractions and negative numbers, the only math skill this course strictly assumes

This course does not teach new arithmetic. It teaches an exact way to
solve many equations at once, without guessing.

---

# Textbooks

<div class="thread">One primary text. Everything else is optional support.</div>

- **Primary:** Lay, Lay & McDonald, *Linear Algebra and Its
  Applications*, 6th ed., Pearson, 2020 (every week's reading points here)
- **References:** Hefferon, *Linear Algebra*, 4th ed. (open textbook);
  Cherney, Denton, Thomas & Waldron, *Linear Algebra*, UC Davis, 2013
- **Also:** these lecture slides themselves are a listed course reference

---

# How This Course Runs

<div class="thread">What to expect from a 3×50-minute block, every week.</div>

Each session mixes short lecture with:

- **A warm-up** - a short, concrete question to start, before any jargon
- **A recap** - what last week delivered, and what it left unsolved
- **Pair activities** - solve a piece of that week's running example,
  with the answer discussed right after
- **A self-check quiz** - ungraded, just for you, at the end

You will talk in this class, not just listen.

---

# Weekly Schedule

<div class="thread">One line per week - the full walkthrough.</div>

| Wk | Topic | Wk | Topic |
|---|---|---|---|
| 1 | Introduction (today) | 9 | Bases, Dimension |
| 2 | Vector & Matrix | 10 | Eigenvalues |
| 3 | Linear Transformation | 11 | Diagonalization - **Assignment 2** |
| 4 | Matrix Algebra - **Assignment 1** | 12 | Orthogonality |
| 5 | Factorization | 13 | Projections |
| 6 | Determinants | 14 | Least Squares - **Quiz 2** |
| 7 | Vector Spaces - **Quiz 1** | 15 | **Final Exam** (Wks 9-14) |
| 8 | **Midterm Exam** (Wks 1-7) | | |

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

<div class="why">
<strong>Grade distribution guideline:</strong> A ≤30%, B ≤40%, C-F ≤30%
of the class. This may shift after the add/drop period, based on final
enrollment.
</div>

<!-- notes: Assignment 1 due Week 4. Assignment 2 due Week 11. Quiz 1 Week 7. Quiz 2 Week 14. -->

---

# Assignments

<div class="thread">Two assignments, spaced across the semester.</div>

| # | Released | Due | Topics |
|---|---|---|---|
| 1 | Wk 2 | Wk 4 | Linear systems, vectors, matrices, matrix algebra |
| 2 | Wk 9 | Wk 11 | Bases, dimension, eigenvalues, diagonalization |

---

# Feedback Policy

<div class="thread">From the syllabus, verbatim.</div>

> Assignments graded within one week with rubric and model answers;
> exam item-analysis shared with weak-topic guidance and individual
> review on request.

In plain terms: you will know what you got wrong, and why, quickly
enough for it to still matter for the next assignment or exam.

---

# Attendance & Late Work

<div class="thread">Concrete rules, stated once, so nobody is surprised later.</div>

- **Attendance** is 10% of your grade and is recorded every session.
- **Late arrival:** arriving within 15 minutes of the start is on-time;
  after that, you're marked late. Three lates equal one absence.
- **Can't attend?** Email the instructor *before* the session to be
  marked excused - unexcused absences aren't eligible for makeup credit.
- **Late work:** loses 10% of that assignment's grade per day late, up
  to 3 days. No credit after 3 days, unless arranged with the
  instructor in advance.

---

# Academic Integrity

<div class="thread">Same principle as attendance: stated once, plainly.</div>

- **Academic integrity:** submit your own work. Copying another
  student's work, having someone else complete it for you, or
  submitting unattributed AI-generated work as your own is a
  violation.
- **First violation:** zero credit on that assignment or exam, plus a
  formal report. **Repeat violation:** may result in failing the
  course, per university policy.
- If anything here is unclear, ask - now is the cheapest time to ask.

---

# Support for Students with Disabilities

<div class="thread">From the syllabus's accommodations section.</div>

- **Hearing-impaired:** front-row seating, lecture material files
  provided where possible, urgent notices given in writing
- **Mobility-impaired:** extended exam time
- **Other documented conditions:** extended exam time, materials
  provided in advance, enlarged exam copies, or other reasonable
  accommodation based on need

Contact the instructor early, and the Disability Student Support
Center or Academic Affairs Team, so accommodations are ready before
you need them.

---

# Contact

<div class="thread">How to reach the instructor.</div>

- **Email:** yushintia@deu.ac.kr
- **Office hours:** by email appointment
- Email is the fastest way to reach the instructor outside of class.

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
