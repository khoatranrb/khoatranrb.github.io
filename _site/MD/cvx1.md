#### **1. Line and line segment:**

* Suppose we have two points $\mathbf{x_1}\neq\mathbf{x_2}$:

  * The line through two this points:
    $$
    \mathbf{y}=\theta\mathbf{x_1}+(1-\theta)\mathbf{x_2} \ \ \ \ \ \ \ \  \forall\theta\in\mathcal{R}\tag1.
    $$

  * The line segment between two this points:
    $$
    \mathbf{y}=\theta\mathbf{x_1}+(1-\theta)\mathbf{x_2} \ \ \ \ \ \ \ \  \forall\theta\in[0,1]\tag2.
    $$

* In another view, we can rewrite two equations above in this form:
  $$
  \mathbf{y}=\mathbf{x_2}+\theta(\mathbf{x_1}-\mathbf{x_2})\tag3
  $$

#### **2. Affine sets:**

* ***Definition***: *A set $\mathbf{C}\in\mathcal{R}^n$ is affine if the line through any two distinct points in $\mathbf{C}$ lies in $\mathbf{C}$.*
  $$
  \begin{align}
  &\mathbf{x_1},\ \mathbf{x_2}\in\mathbf{C}\ ;\\
  &\mathbf{x_1}\neq\mathbf{x_2} \ ; \\
  & \theta\in\mathcal{R} \ ; \\
  & \theta\mathbf{x_1}+(1-\theta)\mathbf{x_2}\in\mathbf{C}\ ;\\
  &\Longrightarrow \text{$\mathbf{C}$ is affine}.
  \end{align}\tag4
  $$

* We can generalize to more than two points:

  *  Assume that $\mathbf{C}$ is a affine set and three distinct points $\mathbf{x_1}$, $\mathbf{x_2}$ and $\mathbf{x_3}$ lie in $\mathbf{C}$. We have:
    $$
    \begin{align}
    [\mathbf{P_1}] \ \ &2\alpha\mathbf{x_2}+(1-2\alpha)\mathbf{x_1}\in\mathbf{C}\\
    [\mathbf{P_2}] \ \ &2\beta\mathbf{x_3}+(1-2\beta)\mathbf{x_1}\in\mathbf{C}\\
    [\frac{1}{2}\mathbf{P_1}+(1-\frac{1}{2})\mathbf{P_2}] \ \ &(1-\alpha-\beta)\mathbf{x_1}+\alpha\mathbf{x_2}+\beta\mathbf{x_3}\in\mathbf{C}.
    \end{align}\tag5
    $$

  * In general, we have *affine combination* $\sum_{i=1}^k\theta_i\mathbf{x_i}\in\mathbf{C}$ where $\sum_{i=1}^k\theta_i=1$ and $\forall_{i=1}^k\mathbf{x_i}\in\mathbf{C}$.

* Given a set $\mathbf{X}$, the set of all affine combination in $\mathbf{X}$ is called the *affine hull* of $\mathbf{X}$, denoted $\textbf{aff}\ \mathbf{X}$:
  $$
  \textbf{aff}\ \mathbf{X}=\biggl\{\sum_{i=1}^k\theta_i\mathbf{x_i}\ \biggl|\ \sum_{i=1}^k\theta_i=1;\ \forall_{i=1}^k\mathbf{x_i}\in\mathbf{X}\biggl\}\tag6.
  $$

  * The affine hull is the smallest affine set that contain $\mathbf{X}$.

#### **3. Affine dimension and relative interior:**

* The affine dimension of a set $\mathbf{X}$ is the dimension of its affine hull.

* If the affine dimension of a set $\mathbf{X}\in\mathcal{R}^{n}$ is $m$ where $m<n$, the set  $\textbf{aff}\ \mathbf{X}\in\mathcal{R}^m$,  we define the relative interior of set $\mathbf{X}$:
  $$
  \textbf{relint}\ \mathbf{X}=\biggl\{\mathbf{x\in X}\ \biggl|\ \mathcal{B}(\mathbf{x},r)\cap\textbf{aff}\ \mathbf{X}\in\mathbf{X} \ \ \text{for $r$>0}\biggl\}\tag7
  $$
  where $\mathcal{B}(\mathbf{x},r)=\{\mathbf{y}\ |\ \lVert\mathbf{y}-\mathbf{x}\rVert<r\}$.

* We the define the relative boundary of a set $\mathbf{X}$ as $\textbf{cl}\ \mathbf{X} \setminus \textbf{relint}\ \mathbf{X}$ where $\textbf{cl}\ \mathbf{C}$ is the closure of $\mathbf{C}$.

* *Example*:

  * Given set $\mathbf{X}$ is the circle with radius 1 lie on $\text{xOy}$ plane in 3-dimensional space:
    $$
    \mathbf{X}=\biggl\{\mathbf{x}\in\mathcal{R}^3\ \biggl|\ \lVert\mathbf{x}\rVert\le1;\ \mathbf{x}^{(z)}=0\biggl\}\tag8.
    $$

  * We have:

    * The affine hull of $\mathbf{X}$:
      $$
      \textbf{aff X}=\biggl\{\mathbf{x}\in\mathcal{R}^3\ \biggl|\ \mathbf{x}^{(z)}=0\biggl\}\tag9.
      $$

    * The relative interior of $\mathbf{X}$:
      $$
      \textbf{relint X}=\biggl\{\mathbf{x}\in\mathcal{R}^3\ \biggl|\ \lVert\mathbf{x}\rVert<1;\ \mathbf{x}^{(z)}=0\biggl\}\tag{10}.
      $$

    * The relative boundary of $\mathbf{X}$:
      $$
      \biggl\{\mathbf{x}\in\mathcal{R}^3\ \biggl|\ \lVert\mathbf{x}\rVert=1;\ \mathbf{x}^{(z)}=0\biggl\}\tag{11}.
      $$



#### **Reference:**

* Chapter 2 | Convex Optimization.

