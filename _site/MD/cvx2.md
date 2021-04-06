#### **1. Convex sets**

* ***Definition 1:*** *A set $\mathbf{C}$ is **convex** if the line segment between any two distinct points in  $\mathbf{C}$ lies in  $\mathbf{C}$.*
    
    * For any $\mathbf{x_1}$, $\mathbf{x_2}$ $\in\mathbf{C}$, $\theta\in[0,1]$, we have $\theta\mathbf{x_1}+(1-\theta)\mathbf{x_2}\in\mathbf{C}$.
* With $\forall_{i=1}^k\mathbf{x}_i\in\mathbf{C}$ and $\begin{cases}\forall_{i=1}^k\theta_i\ge0\\\sum_{i=1}^k\theta_i=1\end{cases}$, we call a point of a form $\sum_{i=1}^k\theta_i\mathbf{x}_i$ is a convex combination.
* As with *affine sets* (mentioned in <a href='https://khoatranrb.github.io/2021/03/15/cvx1' style='color:green'>CVX_1</a>), we can show that a set is convex if it contains every convex combination of its points. So we ignore the proof.
* ***Definition 2:*** *A **convex hull** of a set $\mathbf{X}$, denoted $\text{conv}\mathbf{X}$ is a set of all convex combinations of points in $\mathbf{X}$.*
    $$
    \text{conv}\mathbf{X}=\biggl\{\sum_{i=1}^k\theta_i\mathbf{x}_i \ \biggl|\ \forall_{i=1}^k\mathbf{x}_i\in\mathbf{X},\ \forall_{i=1}^k\theta_i\ge0,\ \sum_{i=1}^k\theta_i=1\biggl\}
    $$
    
#### **2. Cones**
* ***Definition 3:*** *A set $\mathbf{C}$ is called **cone** or **nonnegative homogeneous** if for every $\mathbf{x}\in\mathbf{C}$ and $\theta\ge0$, we have $\theta\mathbf{x}\in\mathbf{C}$.*
* ***Definition 4:*** *A set $\mathbf{C}$ is **convex cone** if it is convex and a cone.*
    
* For any $\mathbf{x_1}, \mathbf{x_2}\in\mathbf{C}$ and $\theta_1,\theta_2\ge0$, we have $\theta_1\mathbf{x_1}+\theta_2\mathbf{x_2}\in\mathbf{C}$.
    
* Similar to convex sets, we can define a point $\sum_{i=1}^k\theta_i\mathbf{x}_i$ is a *conic combination* with $\forall_{i=1}^k\mathbf{x}_i\in\mathbf{C}$ and $\forall_{i=1}^k\theta_i\ge0$. And again, a set is cone if it contains every conic combination of its.
* ***Definition 5:*** *The **conic hull** of a set $\mathbf{X}$ is the set of all conic combinations of points in $\mathbf{X}$*:
    $$
    \biggl\{\sum_{i=1}^k\theta_i\mathbf{x}_i \ \biggl|\ \forall_{i=1}^k\mathbf{x}_i\in\mathbf{X},\ \forall_{i=1}^k\theta_i\ge0\biggl\}
    $$
    *which is also smallest convex cone that contains $\mathbf{X}$.*

#### **Reference:**

* Chapter 2 | Convex Optimization.