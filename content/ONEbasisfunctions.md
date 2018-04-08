Title:Function approximations<!-- In the name of Allah-->
Date:2018-05-7
Category:Blog
----------------------------------
----------------------------------
This blog post discuss about approximating a functional relationship between the given input and the desired output quantity of interest. One possibility of the need for such approximations arises where computing the desired output is very expensive for a given input. For example, the function value may be the outcome of many high fidelity simulations (solving high dimensional partial differential equations) and it may take a lot of computing time to compute one function value. In such situations, the goal
would be to derive a functional approximation in order to obtain (approximate) function values much quicker using only a finite set of data points (training set).

The training set, in which there are $p$ pairs is represented by
\begin{equation}
\mathbf{T} = \lbrace (\mathbf{x}_i, y_i) \rbrace_{i=1}^p
\label{trainingset}
\end{equation}

where $\mathbf{x}_i$, $y_i$ represents the $i$th input vector and output respectively.

Most likely, the model for the function approximation $f(\mathbf{x})$ is expressed as a linear combination of a set of $m$ fixed functions that takes the form

-------------------------------------------------------------

\begin{equation}
f(\mathbf{x}) = \sum_{j=1}^m w_j~h_j(\mathbf{x})
\label{function}
\end{equation}

--------------------------------------------------------------

where $h_j(\mathbf{x})$  is the $j$th fixed function. These fixed functions ($h_j(\mathbf{x})$) are often
called basis functions by analogy with the concept of a vector being composed of a
linear combination of basis vectors. Very often, the basis functions are fixed and the learning problem to determine optimal function approximation for a given training set (Eq. \eqref{trainingset}) involve solving a set of equations for the optimal weight values ($\lbrace w_j \rbrace_{j=1}^m$) implied by the
training set.

There are many classical models ($f(\mathbf{x})$) classified based on the type of basis functions used in Eq. \eqref{function}. Few of the classical set of basis functions  are listed below

1. **Polynomial basis functions**  $h_j(x) = x^j$

2. **Fourier basis functions**  $h_j(x) = \sin(\frac{2 \pi j (x - \theta_j)}{m})$

3. **Wavelet basis functions** $h_j(x) = \exp(i a x) \exp(\frac{-x^2}{2 \sigma})$, $h_j(x) = \frac{1}{\sqrt{2 \pi} \sigma^3} \left( \exp(\frac{-x^2}{2 \sigma}) \cdot (\frac{x^2}{\sigma^2} - 1) \right)$

4. **Radial basis functions** $h_j(x) = \exp(-\frac{x_j - c}{r^2})$, $h_j(x) = \sqrt{\frac{r^2 + (x_j - c)^2}{r}}$

5. **Neural network basis functions** $h_j(x) = \tanh(\mathbf{U}^T x + b)$, $h_j(x) = \frac{1}{1 + \mathbf{U}^T x + b}$
