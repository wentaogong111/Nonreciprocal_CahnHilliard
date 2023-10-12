
---
# Pseudo-spectral Method and High Order Time Integration for Multicomponent Phase Separation

## 1. Pseudo-spectral Discretization in Space

Using the pseudo-spectral method, we represent the spatial derivatives in Fourier space rather than real space. Differentiation becomes multiplication in Fourier space.

For a generic function $ f(r) $, its Fourier transform is given by:
$$ F(k) = \int f(r) e^{-i k \cdot r} dr $$
and its inverse Fourier transform is:
$$ f(r) = \int F(k) e^{i k \cdot r} dk $$

The gradient in Fourier space becomes:
$$ \nabla f(r) \to i k F(k) $$

## 2. Discretization in Time

### 2.1. Runge-Kutta 4th Order (RK4)

The RK4 scheme is:
$$ f_{n+1} = f_n + \frac{\Delta t}{6}(k_1 + 2k_2 + 2k_3 + k_4) $$
where:
$$ k_1 = g(f_n,t_n) $$
$$ k_2 = g(f_n+\frac{\Delta t}{2}k_1, t_n + \frac{\Delta t}{2}) $$
$$ k_3 = g(f_n+\frac{\Delta t}{2}k_2, t_n + \frac{\Delta t}{2}) $$
$$ k_4 = g(f_n+\Delta tk_3, t_n+\Delta t) $$

### 2.2. Fourth-order Adams-Moulton

The implicit method is:
$$ f_{n+3} = f_{n+2} + \frac{\Delta t}{24}[9g(f_{n+3},t_{n+3}) + 19g(f_{n+2},t_{n+2}) - 5g(f_{n+1},t_{n+1}) + g(f_n,t_n)] $$

## 3. Applying to the given equations

### 3.1. Current Dynamics Discretization

In Fourier space:
$$ j_i(k,t) = -\mu^{eq}_i(k,t) -\sum_{j} \alpha_{ij}\phi_{j}(k,t) + \zeta_i(k,t) $$

### 3.2. Chemical Potential in Equilibrium

In Fourier space:
$$ \mu^{eq}_i(k,t) = \frac{\delta F}{\delta \phi_i(k,t)} $$

## 4. Time Evolution

Combining spatial discretization with the RK4 scheme for the first four time steps. Then, use the Adams-Moulton method.

---

**Note:** The exact implementation requires considerable coding effort and domain knowledge. For complex problems like this, solvers often require iterative methods, preconditioners, and other numerical techniques. If you need code, you'll need a specific programming environment or library, like FFTW for Fourier transforms.

# Active Binary Mixture Simulation

This document describes the simulation of an active binary mixture using the provided conservation laws and current dynamics. 

## 2.1 Conservation Law

Given the equation:
$$ \partial_t \phi_i + \nabla \cdot j_i = 0 $$
in Fourier space it becomes:
$$ \partial_t \hat{\phi}_i + i \mathbf{k} \cdot \hat{j}_i = 0 $$
where $ \hat{} $ denotes the Fourier transform of the function.

**Processes of transform this equation into Fourier space**
$$ \hat{f}(k) = \int f(r) e^{-i k \cdot r} dr $$

$$ \hat{f}(k_x, k_y, k_z) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x, y, z) e^{-i(k_x x + k_y y + k_z z)} dx dy dz $$

$$ f(r) = \int \hat{f}(k) e^{i k \cdot r} dk $$

$$ f(x, y, z) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \hat{f}(k_x, k_y, k_z) e^{i(k_x x + k_y y + k_z z)} dk_x dk_y dk_z $$

For a gradient, the Fourier transform of the gradient of a function $ f $ is:

$$ \nabla f \rightarrow i \mathbf{k} \hat{f} $$

where $ \mathbf{k} = (k_x, k_y, k_z) $ is the wavevector.


## 2.2 Current Dynamics

Given:
$$ j_i = -\nabla \mu^{eq}_i -\sum_{j} \alpha_{ij}\nabla\phi_{j} + \zeta_i $$
**Chemical Potential in Equilibrium**: 
$$ \mu^{eq}_i = \frac{\delta F}{\delta \phi_i} $$


**Effective Nonequilibrium Chemical Potential**

$$ \mu_{i}^{neq}= \mu_{i}^{eq} + \sum_{j=1}^{N}\alpha_{ij}\phi_j  $$

For a binary mixture, the free energy can be written as
$$ F = \int d \mathbf{r} \left[ \sum_{i=1}^{2}(\phi_i-c_{i,1})^2(\phi_i-c_{i,2})^2 + (\chi_{ij}\phi_i\phi_j+\chi^{'}\phi_i^2\phi_j^2)+\sum_{i=1}^{2}\frac{k_{i}}{2}|\nabla_{i}|^2 \right] $$

which results in equilibrium chemical potentials
$$ \mu_{1}^{eq} =2(\phi_1-c_{1,1})(\phi_1-c_{2,2})(2\phi_1-c_{1,1}-c_{1,2})+\chi\phi_2+2\chi^{'}\phi_1\phi_2^2
$$
$$ \mu_{2}^{eq} =2(\phi_1-c_{2,1})(\phi_1-c_{2,2})(2\phi_1-c_{2,1}-c_{2,2})+\chi\phi_1+2\chi^{'}\phi_2\phi_1^2
$$


When transforming into the Fourier domain using the general rule:
$$ \nabla f \rightarrow i \mathbf{k} \hat{f} $$

The transformed current dynamics becomes:
$$ \hat{j}_i = i \mathbf{k} \hat{\mu}^{eq}_i + \sum_{j} \alpha_{ij} i \mathbf{k} \hat{\phi}_j + \hat{\zeta}_i $$

Where:
- $ \hat{\mu}^{eq}_i $ represents the Fourier transform of $ \mu^{eq}_i $.
- $ \hat{\phi}_j $ is the Fourier transform of $ \phi_j $.
- $ \hat{\zeta}_i $ is the Fourier transform of $ \zeta_i $.
- the effective nonequilibrium chemical potential transformation in the Fourier domain is $ \hat{\mu}_{i}^{neq} = \hat{\mu}_{i}^{eq} + \sum_{j=1}^{N} \alpha_{ij} \hat{\phi}_j $


The two-dimensional Fourier-transformed equation is given by:
$$
\hat{j}_i = -i k_x \hat{\mu}^{eq}_i - \sum_{j} \alpha_{ij} i k_x \hat{\phi}_j - i k_y \hat{\mu}^{eq}_i - \sum_{j} \alpha_{ij} i k_y \hat{\phi}_j + \hat{\zeta}_i
$$
For the component $i = 1$:

$$ \hat{j}_1(k_x, k_y) = -i k_x \hat{\mu}^{eq}_1(k_x, k_y) - \alpha_{11} i k_x \hat{\phi}_1(k_x, k_y) - \alpha_{12} i k_x \hat{\phi}_2(k_x, k_y) - i k_y \hat{\mu}^{eq}_1(k_x, k_y) - \alpha_{11} i k_y \hat{\phi}_1(k_x, k_y) - \alpha_{12} i k_y \hat{\phi}_2(k_x, k_y) + \hat{\zeta}_1(k_x, k_y) $$

For the component $i = 2$:

$$ \hat{j}_2(k_x, k_y) = -i k_x \hat{\mu}^{eq}_2(k_x, k_y) - \alpha_{21} i k_x \hat{\phi}_1(k_x, k_y) - \alpha_{22} i k_x \hat{\phi}_2(k_x, k_y) - i k_y \hat{\mu}^{eq}_2(k_x, k_y) - \alpha_{21} i k_y \hat{\phi}_1(k_x, k_y) - \alpha_{22} i k_y \hat{\phi}_2(k_x, k_y) + \hat{\zeta}_2(k_x, k_y) $$

Here, 
- $ \hat{j}_i $ represents the Fourier-transformed current for the i-th component.
- $ k_x $ and $ k_y $ are the wavevectors in the x and y directions, respectively.
- $ \hat{\mu}^{eq}_i $, $ \hat{\phi}_j $, and $ \hat{\zeta}_i $ are the Fourier-transformed versions of equilibrium chemical potential, phase field, and random noise, respectively.
- $ \alpha_{ij} $ is the interaction coefficient between the i-th and j-th components.




# Numerical simulation


# Step-by-Step Approach to Solve the System:

## 1. Initialization:

- **Define the grid:** Choose the spatial step h, grid size N, and generate the meshgrid for Fourier wave numbers \(k_x\) and \(k_y\).

- **Initial conditions:** Provide the initial fields \(\phi_1\) and \(\phi_2\) in real space. Compute the Fourier transform to get \(\hat{\phi}_i\).

- **Define constants:** Specify interaction parameters such as \(\chi\), \(\chi'\), and \(c\) values.

- **Initialize source terms:** Precompute any external source terms or factors that don't change over time.

## 2. Time Marching:

- **Choose a time-stepping scheme:** You provided both the RK4 and Adams-Moulton methods. RK4 might be a good starting point due to its simplicity and stability, but the Adams-Moulton method might provide better performance for stiff problems.

  - **a. Compute the Equilibrium Chemical Potentials:** Evaluate \(\mu^{eq}_i\) in real space using the provided `compute_equilibrium_chemical_potentials` function.

  - **b. Fourier transform** of \(\mu^{eq}_i\) and \(\phi_i\): Convert these fields into Fourier space.

  - **c. Compute the Current \(j_i\)** in Fourier space: This is calculated using the function `compute_j_fourier`. The function accounts for both linear and nonlinear terms. It also includes the white noise \(\zeta\) which needs to be freshly generated from a Gaussian distribution at every time step.

  - **d. Solve for \(\hat{\phi}_i\)** in the next time step: This involves integrating the provided equation in Fourier space using either the RK4 or Adams-Moulton method.

  - **e. Inverse Fourier transform:** Convert the updated \(\hat{\phi}_i\) back to real space to get the updated fields \(\phi_i\).

  - **f. Check Convergence:** As you simulate more components, ensuring stability becomes crucial. Continuously decrease the time step until the simulation results converge to a steady state. One criterion for checking convergence can be the norm of the difference between two consecutive time steps.


