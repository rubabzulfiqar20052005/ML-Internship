# Task 1 — NumPy Matrix Operations

## Description
Write a script that creates two random matrices, 
performs element-wise and matrix multiplication, computes the inverse and determinant 
of a square matrix, normalises a 1D array to range [0,1], and uses broadcasting to 
subtract the column mean from each column of a 2D array. Print shapes and results at 
every step with descriptive labels. 

## Libraries Used
- **NumPy** — matrix creation, mathematical and linear algebra operations

## Concepts & Functions Used
| Concept | Function |
|---------|---------|
| Random matrix creation | `np.random.randint()` |
| Element-wise multiplication | `A * B` |
| Matrix multiplication | `np.matmul(A, B)` |
| Determinant | `np.linalg.det()` |
| Inverse | `np.linalg.inv()` |
| Normalization | `(x - min) / (max - min)` |
| Broadcasting | `matrix - col_mean` |
