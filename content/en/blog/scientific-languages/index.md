---
title: Languages of scientific computing
summary: Why Fortran is still alive in numerical work, what the two-language problem is, and what Julia is trying to do about it.
date: 2026-09-04
authors:
  - me
tags:
  - Python
  - C++
  - Fortran
  - Julia
---

## What counts as a language for scientific computing

There is no separate class of languages "for science" — there are languages in
which it became customary to compute. The requirements of such tasks are
specific: operations over large arrays of numbers, predictable performance and,
most importantly, trust in the result.

The last of these explains how conservative the field is. A library that has
been verified for forty years does not get rewritten because a more convenient
syntax has appeared.

## Fortran, which never died

The first high-level language, 1957. It is regularly declared dead, and it
regularly turns out to be running underneath everything else.

The reason is concrete: BLAS and LAPACK, the linear algebra libraries written
in Fortran and polished over decades. When two matrices are multiplied in
Python through NumPy, the call eventually reaches compiled code descending from
those libraries.

Fortran has not gone anywhere — it has simply stopped being the language users
write in.

## The two-language problem

Hence the familiar way of working: the prototype is written in a convenient
language, and the bottleneck is rewritten in a fast one.

It is convenient to explore hypotheses in Python, but a loop over a million
elements is slow there. So the critical section moves to C, C++ or Fortran,
and Python remains the layer that glues those sections together.

The scheme works, but it has a price. You need to know two languages. You need
to maintain the boundary between them. And debugging becomes harder: an error
may be in the script, in the compiled kernel, or in how the two call each
other.

In the literature this is known as the two-language problem.

## Where each language is used

**Python** is the glue. On its own it is unsuitable for computation, but NumPy,
SciPy and PyTorch give access to compiled kernels through a convenient
interface. Python's real job here is to organise the computation, not to
perform it.

**C and C++** are used where control over memory and predictable execution time
matter. The computational kernels themselves are written in them. In my own
project with a local code generation agent the language model runs through
llama.cpp — exactly this case: a C++ library called from a program.

**R** and **MATLAB** are domain-specific: the first in statistics, the second
in engineering computation. Both are strong in ready-made packages within their
domain and of little use outside it.

**Julia** is an attempt to remove the two-language problem. The language was
designed so that code with dynamic syntax is compiled to machine code just
before execution. The idea is that the prototype and the production version are
the same code.

## What follows from this

Choosing a language for a scientific task means choosing where to draw the line
between convenience of expression and speed of execution.

While the task is exploratory and the data small, the line may not be needed at
all. Once a computation starts taking hours, it appears by itself, and the only
question is whether it ends up inside one language or between two.
