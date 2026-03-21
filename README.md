# Low-Depth QAOA for Portfolio Optimization

This project implements a **low-depth Quantum Approximate Optimization Algorithm (QAOA)** for solving a **portfolio optimization problem** using a QUBO (Quadratic Unconstrained Binary Optimization) formulation.

The focus is on:
- Efficient **Hamiltonian construction**
- **QUBO encoding with budget constraints**
- Running **QAOA at low circuit depth (NISQ-friendly)**
- Comparing optimization strategies

---

## Problem Overview

We aim to select a subset of assets that:

- Maximizes expected return (upside)
- Satisfies a fixed investment budget

This is formulated as a **binary optimization problem**:

$\[
\max \sum_i v_i x_i
\]$

Subject to:

\[
\sum_i w_i x_i \leq B
\]

Where:
- \( x_i \in \{0,1\} \) → select asset or not  
- \( v_i \) → expected return  
- \( w_i \) → allocation cost  
- \( B \) → total budget  

---

## QUBO Formulation

The constrained problem is converted into QUBO using a penalty:

\[
H = -\sum_i v_i x_i + P \left(\sum_i w_i x_i - B\right)^2
\]

To encode the inequality constraint, **slack variables** are introduced:

\[
\sum_i w_i x_i + \sum_k 2^k s_k = B
\]

This ensures the constraint is satisfied exactly.

---

## Key Features

- QUBO → Ising Hamiltonian conversion  
- Binary slack encoding for budget constraint  
- Scaled encoding to reduce qubit count  
- Low-depth QAOA circuits (NISQ-compatible)  
- Classical optimizer integration (COBYLA, Powell, etc.)  
- Cost tracking and visualization  

---

## Example Output

- Selected assets (bitstring)
- Best QUBO value
- Expected portfolio return
- Cost history across iterations

---

## Project Structure
