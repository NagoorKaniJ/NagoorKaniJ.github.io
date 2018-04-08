Title:Theorems in Linear Algebra<!-- In the name of Allah-->
Date:2018-02-23
Category:Blog
----------------------------------
----------------------------------

>
If $\mathbf{Q} \in \mathbb{R}^{n \times n}$ is orthogonal, then for all $\mathbf{x}$, $\mathbf{y}$ $\in \mathbb{R}^n$,
\begin{equation*}
\begin{aligned}
\langle \mathbf{Q} \mathbf{x}, \mathbf{Q} \mathbf{y} \rangle &= \langle \mathbf{x}, \mathbf{y} \rangle \\
\Vert \mathbf{Q} \mathbf{x} \Vert_2 &= \Vert \mathbf{x}  \Vert_2
\end{aligned}
\end{equation*}

----------------------------------

>
Let $\mathbf{A} \in \mathbb{R}^{n \times n}$. Then there exists an orthogonal matrix $\mathbf{Q}$  and an upper triangular matrix $\mathbf{R}$  such that $\mathbf{A} = \mathbf{Q}  \mathbf{R}$.


>
Let  $\mathbf{u} \in \mathbb{R}^n$ with $\Vert \mathbf{u}  \Vert_2 = 1$, and define $\mathbf{P} \in \mathbb{R}^{n \times n}$ by  $\mathbf{P} = \mathbf{u}  \mathbf{u}^T$. Then
\begin{equation*}
\begin{aligned}
\mathbf{P} \mathbf{u} &=  \mathbf{u} \\
\mathbf{P} \mathbf{v} &= 0 \: \text{if} \: \langle \mathbf{u}, \mathbf{v} \rangle = 0 \\
\mathbf{P}^2  &=  \mathbf{P} \\
\mathbf{P}^T  &=  \mathbf{P} \\
\mathbf{P} &= \: \text{is a rank 1 ortho projector}
\end{aligned}
\end{equation*}

----------------------------------

>
Let  $\mathbf{u} \in \mathbb{R}^n$ with $\Vert \mathbf{u}  \Vert_2 = 1$, and define $\mathbf{Q} \in \mathbb{R}^{n \times n}$ by  $\mathbf{Q} = \mathbf{I} - 2 \mathbf{u}  \mathbf{u}^T$. Then
\begin{equation*}
\begin{aligned}
\mathbf{Q} \mathbf{u} &=  -\mathbf{u} \\
\mathbf{Q} \mathbf{v} &= v \: \text{if} \: \langle \mathbf{u}, \mathbf{v} \rangle = 0 \\
\mathbf{Q}  &=  \mathbf{Q}^T  (\text{symmetric}) \\
\mathbf{Q}^{-1}  &=  \mathbf{Q}^T (\text{orthogonal}) \\
\mathbf{Q}^{-1}  &=  \mathbf{Q} (\text{involution}) \\
\mathbf{Q} &= \: \text{is reflector or Householder transformation}
\end{aligned}
\end{equation*}

----------------------------------

> Let $\mathbf{x}$, $\mathbf{y}$ $\in \mathbb{R}^n$,  with $\mathbf{x} \neq$,  $\mathbf{y}$,  but $\Vert \mathbf{x} \Vert = \Vert \mathbf{y} \Vert$. Then there is a
unique reflector $\mathbf{Q}$ such that $\mathbf{Q} \mathbf{x} =  \mathbf{y}$.

> Let $\mathbf{A} \in \mathbb{R}^{n \times n}$  be nonsingular. There there exist unique $ \mathbf{Q}$, $\mathbf{R}  \in \mathbb{R}^{n \times n}$  such that $\mathbf{Q}$ is orthogonal, $\mathbf{R}$ is upper triangular with positive main-diagonal
entries, and $\mathbf{A} = \mathbf{Q}  \mathbf{R}$.

----------------------------------

> Consider an overdetermined system
\begin{equation*}
\begin{aligned}
\mathbf{A} \mathbf{x} &= \mathbf{b} \: \mathbf{A} \in \mathbb{R}^{n \times m} \: \mathbf{b} \in \mathbb{R}^n, n > m \\
\mathbf{r} &=  \mathbf{A} \mathbf{x} - \mathbf{b} \\
\mathbf{s} &= \mathbf{Q}^T~\mathbf{A} \mathbf{x} - \mathbf{Q}^T~\mathbf{b} \\
\Vert \mathbf{s} \Vert_2 &= \Vert \mathbf{r} \Vert_2
\end{aligned}
\end{equation*}

----------------------------------

> Let $\mathbf{A} \in \mathbb{R}^{n \times m}$, $n > m$. Then there exist $\mathbf{Q} \in \mathbb{R}^{n \times n}$  and $\mathbf{R} \in \mathbb{R}^{n \times m}$ , such that $\mathbf{Q}$ is orthogonal and $\mathbf{R} = [\hat{\mathbf{R}} \: 0]$
where $\hat{\mathbf{R}} \in \mathbb{R}^{m \times m}$ is upper
triangular, and $\mathbf{A} = \mathbf{Q}  \mathbf{R}$.

----------------------------------

> Let $\mathbf{A} \in \mathbb{R}^{n \times m}$,  $n > m$, $\mathbf{b} \in \mathbb{R}^n$ and suppose $\mathbf{A}$ has full rank.
Then the least squares problem for the overdetermined system $\mathbf{A} \mathbf{x} = \mathbf{b}$ has a unique
solution, which can be found by solving the nonsingular system $\hat{\mathbf{R}} \mathbf{x} = \hat{\mathbf{c}}$, where $\mathbf{c} = [\hat{\mathbf{c}} \: 0] = \mathbf{Q}^T~\mathbf{b}$, $\hat{\mathbf{R}} \in \mathbb{R}^{m \times m}$.

----------------------------------

> Let $\mathbf{A} \in \mathbb{R}^{n \times m}$,  $n > m$, $\mathbf{b} \in \mathbb{R}^n$. Then the least squares
problem for the overdetermined system $\mathbf{A} \mathbf{x} = \mathbf{b}$ always has a solution. If $\mathbf{A} <
m,$ there are infinitely many solutions.

----------------------------------

> Let $\mathbf{S}$ be any subset of $\mathbb{R}^{n}$. The orthogonal complement of $\mathbf{S}$, denoted $\mathbf{S}^{\perp}$, is defined to be the set of vectors in $\mathbb{R}^{n}$ that are orthogonal to $\mathbf{S}$. Then for every $\mathbf{x} \in \mathbb{R}^{n}$, there exist unique elements $\mathbf{s} \in \mathbf{S}$ and $\mathbf{s}^{\perp} \in \mathbf{S}^{\perp}$ for which $\mathbf{x} = \mathbf{s} + \mathbf{s}^{\perp}$.

----------------------------------

> Let $\mathbf{S}$ be any subset of $\mathbb{R}^{n}$ and $\mathbf{b} \in \mathbb{R}^n$. Then there exist unique $\mathbf{y} \in \mathbf{S}$ such that
\begin{equation*}
\Vert \mathbf{b} - \mathbf{y} \Vert_2 = \min_{\mathbf{s} \in \mathbf{S}} \Vert \mathbf{b} - \mathbf{s} \Vert_2
\end{equation*}
$\mathbf{y} \in \mathbf{S}$ is unique such that $\mathbf{b} - \mathbf{y} \in \mathbf{S}^{\perp}$. In other words, $\mathbf{y}$ is the orthogonal projection of $\mathbf{b}$ into $\mathbf{S}$. Since the least-square problem is to find $\mathbf{x} \in \mathbb{R}^{m}$ such that
\begin{equation*}
\Vert \mathbf{b} - \mathbf{A} \mathbf{x} \Vert_2 = \min_{\mathbf{w} \in \mathbb{R}^{m}} \Vert \mathbf{b} - \mathbf{A} \mathbf{w} \Vert_2
\end{equation*}

----------------------------------

> Let $\mathbf{A} \in \mathbb{R}^{n \times m}$ be a nonzero matrix with rank $r$.
Then $\mathbf{A}$ can be expressed as a product
\begin{equation*}
\mathbf{A} = \mathbf{U} \mathbf{\Sigma} \mathbf{V}^T
\end{equation*}
where$\mathbf{U} \in \mathbb{R}^{n \times n}$ and $\mathbf{V} \in \mathbb{R}^{m \times m}$ are orthogonal, and $\mathbf{\Sigma} \in \mathbb{R}^{n \times m}$ is a nonsquare diagonal matrix.

----------------------------------

> Let $\mathbf{A} \in \mathbb{R}^{n \times m}$ be a nonzero matrix
with rank $r$. Then $\mathbb{R}^{m}$ has an orthonormal basis $\mathbf{v}_1 \cdots \mathbf{v}_m$, $\mathbb{R}^{n}$ has an orthonormal basis $\mathbf{u}_1 \cdots \mathbf{u}_n$ and there exist $\sigma_1 \geq \sigma_2 \geq \cdots \geq \sigma_r > 0$ such that
\begin{equation*}
\mathbf{A} \mathbf{v}_i=
\begin{cases}
\sigma_i \mathbf{u}_i & \text{$i = 1 \cdots r$,}\\
0 &
\text{$i=r+1 \cdots m$.}
\end{cases} \quad
\mathbf{A}^T \mathbf{u}_i=
\begin{cases}
\sigma_i \mathbf{v}_i & \text{$i = 1 \cdots r$,}\\
0 &
\text{$i=r+1 \cdots n$.}
\end{cases}
\end{equation*}

----------------------------------
