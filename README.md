# Finite element model (FEM) updating problem

## Formulation
Formulation of a FEM updating problem that aims to minimize the largest deviation from experimental values is: 
```math
\begin{align}
    \min_{\mathbf{\alpha}, \mathbf{\lambda}, \mathbf{\psi}, \delta} \quad & \delta \\
    \text{s.t.} \quad 
    & (\mathbf{K}(\mathbf{\alpha}) - \lambda_i \mathbf{M}) \mathbf{\psi}_i = 0 && \forall i \in [n_{\text{modes}}]\\
    & -\delta \le \frac{\lambda_i^{\text{EXP}} - \lambda_i}{\lambda_i^{\text{EXP}}}\cdot w_{\lambda_i} \le \delta && \forall i \in [n_{\text{modes}}] \\
    & - \delta \le (\mathbf{\psi}_{i}^{\text{EXP},\mathcal{M}} - \mathbf{\psi}_{i}^\mathcal{M})\cdot w_{\mathbf{\psi}_i} \le \delta && \forall i \in [n_{\text{modes}}]\\
    & \mathbf{\alpha}_{lb} \le \mathbf{\alpha} \le \mathbf{\alpha}_{ub} \\
    & \mathbf{\psi}_{lb} \le \mathbf{\psi} \le \mathbf{\psi}_{ub} \\
    & \mathbf{\lambda}_{lb} \le \mathbf{\lambda} \le \mathbf{\lambda}_{ub}.
\end{align}
```
This problem can be reformated to a bilinear bipartite problem in the following form with appropriate affine transformations:
```math
\begin{align}
    \min_{\mathbf{x}, \mathbf{y}} \quad & f^\top x + g^\top y \\
    \text{s.t.} \quad 
    & x^\top Q_k y + a_k^\top x + b_k^\top y +c_k = 0 && \forall k \in [m] \\
    & x \in [0,1]^{n_1}, \; y \in [0,1]^{n_2}.
\end{align}
```
