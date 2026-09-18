# Numerical PDEs Homework #0
Trin Wasinger | 20206-09-16

---
## Problem #1
<p align="center">
  <img src="content/problem1.1.png" />
  <br>
  <b>Figure 1.1: Comparison of exact and numeric 2nd derivatives</b>
</p>
<p align="center">
  <img src="content/problem1.2.png" />
  <br>
  <b>Figure 1.2: Error of derivative approximation</b>
</p>

As seen in Figure 1.1, the numeric approximation for $f_x = \frac{d}{dx} e^{\sin x}$ closely matches the actual derivative; however, note the less accurate end points since only first order forward and back differences were used there while the interior points used a centered difference.

In Figure 1.2, we see that the max error ($p=\infty$) is $O(\frac{1}{N})$ as expected (limited by the first order methods on end points). The average error ($p=2$) is approximatly $O(\frac{1}{N^{3/2}})$ since the second order internal points improve the overall statistic but not enough to make it itself second order.

## Problem #2
<p align="center">
  <img src="content/problem2.1.png" />
  <br>
  <b>Figure 2.1: Comparison of exact and numeric 2nd derivatives</b>
</p>
<p align="center">
  <img src="content/problem2.2.png" />
  <br>
  <b>Figure 2.2: Second order error of 2nd derivative approximation</b>
</p>

Using periodicity, the approximation in Figure 2.1 is no longer less acurate at the endpoints than it is internally like was the case in Problem 1. As seen in Figure 2.2, both the max and average error are second order as expected.


## Problem #3
<p align="center">
  <img src="content/problem3.1.png" />
  <br>
  <b>Figure 3.1: Comparison of exact and numeric ODE solutions</b>
</p>
<p align="center">
  <img src="content/problem3.2.png" />
  <br>
  <b>Figure 3.2: Second order error of ODE solution</b>
</p>

With a manufactured solution $u(x) = \sin(x)$,  $f(x) = \cos(x)\sin(x)$, $u_0 = \sin 0$, and $u_N = sin(5)$. As shown in Figure 3.2, the approximation is second order.


## Problem #4
### Part 1
> NOTE: My editor's AI autocomplete suggested a large portion of the boundary implementation (completly unprompted) as I started writing the first loop.
> It was more or less exactly what I was going to type anyways, but I am not sure how I feel about it. I've since found the setting to turn it off.

<p align="center">
  <img src="content/problem4.1-c.png" />
  <br>
  <b>Figure 4.1: Comparison of exact and numeric Poisson Equation solutions</b>
</p>
<p align="center">
  <img src="content/problem4.2.png" />
  <br>
  <b>Figure 4.2: Second order error of numeric Poisson Equation solution</b>
</p>

Figure 4.1 shows the known $u$ and the numeric solution. An intentionally small $N$ was chosen so that the approximation is visually different. Paired filled contour plots seemed like the best way to visualize differences in the two surfaces. Figure 4.2 shows that the approximation is second order for both max and average error.

### Part 2

With only Neumann boundary conditions, the resulting matrix is singular and solutions can have a $\pm c$; the PDE problem we want to solve is under-defined (similar to what we saw in class with periodic boundaries). Fixing a single boundary point with a Dirichlet condition should fix this.

I think I ran into a similar problem last year while working on a [gamedev project](https://github.com/SteveBeeblebrox/Minceraft/blob/c22b0dfe6ad8c4da79768b817211555b83d1d3eb/World.hpp#L191-L194), and my solution then was also to fix points.