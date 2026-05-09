# MIPS Assembly — Linear Equations Solver (Cramer's Rule)

![Language](https://img.shields.io/badge/Language-MIPS%20Assembly-red?style=flat-square)
![Simulator](https://img.shields.io/badge/Simulator-MARS%20%7C%20QtSpim-blue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-success?style=flat-square)

A MIPS32 Assembly implementation of a 3×3 linear equations solver using Cramer's Rule. The program accepts user-defined coefficients at runtime and computes the exact solution using determinant-based arithmetic. Developed as a Computer Organization course project at Birzeit University.

---

## Table of Contents

- [Overview](#overview)
- [Algorithm](#algorithm)
- [Files](#files)
- [Getting Started](#getting-started)
- [Example](#example)
- [Implementation Notes](#implementation-notes)

---

## Overview

Given a 3×3 system of linear equations of the form:

```
a₁x + b₁y + c₁z = d₁
a₂x + b₂y + c₂z = d₂
a₃x + b₃y + c₃z = d₃
```

The program computes the determinant of the coefficient matrix **D**, and the three substituted matrices **Dₓ**, **D_y**, and **D_z**, then applies Cramer's Rule to solve for x, y, and z.

---

## Algorithm

```
1. Read 12 integer coefficients from the user (a, b, c, d for each of 3 equations)
2. Compute det(D)   — coefficient matrix determinant
3. Compute det(Dₓ)  — replace column 1 with constants
4. Compute det(D_y) — replace column 2 with constants
5. Compute det(D_z) — replace column 3 with constants
6. Solve:
     x = Dₓ / D
     y = D_y / D
     z = D_z / D
7. If D = 0 → print "No unique solution"
```

Determinants are computed via cofactor expansion of the 3×3 matrix.

---

## Files

| File | Description |
|------|-------------|
| `final_view.asm` | Main MIPS Assembly source code |
| `ENCS4370_Project1_Fall_2024_2025.pdf` | Original project specification |

---

## Getting Started

### Prerequisites

- [MARS MIPS Simulator](http://courses.missouristate.edu/kenvollmar/mars/) (recommended) or QtSpim

### Run

1. Open MARS and go to **File → Open** → select `final_view.asm`
2. Click **Assemble** (F3)
3. Click **Run** (F5)
4. Enter the 12 integer coefficients when prompted in the console
5. The solution (x, y, z) is printed to the output pane

---

## Example

**Input:**
```
Equation 1: 2  1  -1  8
Equation 2: -3 -1  2  -11
Equation 3: -2  1  2  -3
```

**Output:**
```
x = 2
y = 3
z = -1
```

---

## Implementation Notes

- Written in MIPS32 Assembly using standard syscalls for integer I/O
- Integer arithmetic only — no floating-point registers used
- Handles the degenerate case where `det(D) = 0` (no unique solution)
- Register usage follows standard MIPS calling conventions (`$t`, `$s`, `$a`, `$v` registers)

---

> **Course:** Computer Organization & Assembly Language (ENCS4370) — Computer Engineering Department, Birzeit University
