
# Active Model B+

# Active Model B+

Active Model B+ builds upon the traditional Model B by incorporating effects arising from active particles or out-of-equilibrium systems. In the context of active systems, 'active' refers to individual entities in the system consuming energy to perform some form of mechanical work, such as bacteria swimming in a fluid or synthetic active colloids.

## Key Terms and Concepts:

- **Active Current, $j$:** This is a measure of the flow or motion in the system due to active forces. For example, if you imagine a group of bacteria moving in one direction, they create an active current.

- **Macroscopic Phase Separation:** It refers to the system's tendency to separate into large distinct domains of similar entities. Imagine oil and water in a jar; given enough time, you'll find all the oil clustered together on top of the water – that's macroscopic phase separation.

- **Microphase Separation:** This is when the system breaks into smaller, frequently recurring domains. Think about a striped pattern where the stripes are very close together.

- **Ostwald Ripening:** Over time, in a system of droplets or particles, smaller entities tend to dissolve, and their material gets redeposited onto larger entities. This makes big droplets/particles grow bigger and small ones disappear – a process named after Wilhelm Ostwald.

- **Reversed Ostwald Ripening:** This is the opposite. Smaller entities grow at the expense of larger ones.
---
### Ostwald Ripening: An Overview**

Ostwald ripening is a spontaneous process that arises due to differences in solubility between small and large particles or droplets. It's a common occurrence in systems with a dispersed phase, such as emulsions or suspensions. The primary driving force is the reduction in the system's total surface energy.

---

- **1.  Theory and Concept**

    At a microscopic level, the surface of a particle or droplet has a higher energy than its interior. This is because atoms or molecules on the surface aren't as surrounded by like atoms or molecules as those in the interior, leading to increased surface energy. Due to this heightened energy, particles strive to minimize their surface area.

    However, the surface-to-volume ratio of a small particle is greater than that of a larger particle. Consequently, small particles have a higher energy (per unit volume) compared to larger ones. This energy difference leads to a higher solubility for smaller particles. As a result, molecules from small particles tend to dissolve and then redeposit onto larger particles, leading to the growth of the latter at the expense of the former.


- **2. Equations**

    One of the main equations governing Ostwald ripening is the Lifshitz-Slyozov-Wagner (LSW) theory for the growth rate of particles. For a system with a given volume fraction of the dispersed phase, the radius $ r $ of a particle will change over time $ t $ as:

    $$ r(t)^3 - r_0^3 = Kt $$

    Where:
    - $r_0$ is the initial average radius of the particles.
    - $K$ is a constant that depends on factors like temperature, the volume fraction of the dispersed phase, and the solubility of the particles.



- **3.Properties**

    1. **Particle Size Distribution**: Ostwald ripening leads to a broader particle size distribution over time. Initially small particles shrink, while the larger ones grow.
    2. **Irreversibility**: Once initiated, Ostwald ripening is generally irreversible. The only way to revert to a state of smaller particles would involve external inputs, such as increased energy or the addition of surfactants.
    3. **Dependency on Temperature**: The rate of Ostwald ripening increases with temperature. This is because solubility differences and diffusion rates generally rise with temperature.


- **4.Mitigation**

    To prevent or slow down Ostwald ripening, one can:
    - Use surfactants or stabilizers to modify interfacial properties.
    - Decrease the temperature to reduce the solubility difference and slow down diffusion.
    - Opt for a coarser initial particle size distribution.


    In summary, Ostwald ripening is a thermodynamically driven process where smaller particles dissolve in favor of larger ones, leading to changes in particle size distribution over time. Understanding this phenomenon is crucial in various industries to ensure the stability and performance of products.

---
## Equations
### **2.1 Conservation Law**
Given by:

$$ \partial_t \phi_i + \nabla \cdot j_i = 0 $$
This equation maintains that the number of particles of the $ i^{th} $species is conserved.

### **2.2 Current Dynamics**
Given by:

$$ j_i = -\nabla \mu^{eq}_i -\sum_{j} \alpha_{ij}\nabla\phi_{j}+ \zeta_i $$ 
Here, the term proportional to $\alpha_{ij}$ is a manifestation of nonreciprocity in the system. $\alpha_{ij}$ is a matrix that is fully antisymmetric, denoting nonreciprocal interactions.


**Chemical Potential in Equilibrium**:  
$$ \mu^{eq}_i = \frac{\delta F}{\delta \phi_i} $$

The chemical potential in equilibrium is derived from the free-energy functional $F[\{\phi_i\}]$.


The simplest free energy that can be used to describe
multicomponent phase separation is the Ginzburg-Landau type free energy
The Ginzburg-Landau free energy is given by:
$$ F = \int d \mathbf{r} \left[ \sum_{i=1}^{N}(\phi_i-c_{i,1})^2(\phi_i-c_{i,2})^2 + \sum_{i=1}^{N-1}\sum_{j=i+1}^{N}(\chi_{ij}\phi_i\phi_j+\chi^{'}\phi_i^2\phi_j^2)+\sum_{i=1}^{N}\frac{k_{i}}{2}|\nabla_{i}|^2 \right] $$




#### 1. Local Free Energy Term

$ \sum_{i=1}^{N}(\phi_i-c_{i,1})^2(\phi_i-c_{i,2})^2 $

- **Order Parameter, $\phi_i$:** Represents the degree of order for the $i$-th component.
- **Double-well Potential:** The system has a preference for the order parameter to be close to either $c_{i,1}$ or $c_{i,2}$, resulting in phase separation.

#### 2. Interaction Term between Components

$ \sum_{i=1}^{N-1}\sum_{j=i+1}^{N}(\chi_{ij}\phi_i\phi_j+\chi^{'}\phi_i^2\phi_j^2) $

- **Flory-Huggins Interaction Parameter, $\chi_{ij}$:** Describes the interaction between components $i$ and $j$. Positive values lead to phase separation.

- **Binary Interaction Term, $\chi_{ij}\phi_i\phi_j$:** Contributes to energy based on the product of the order parameters.
- **Higher-order Interaction Term, $\chi^{'}\phi_i^2\phi_j^2$:** Accounts for more complex interactions between components.

#### 3. Gradient Term

$ \sum_{i=1}^{N}\frac{k_{i}}{2}|\nabla_{i}|^2 $

- **Gradient, $\nabla_{i}$:** Measures the spatial variation of the order parameter for the $i$-th component.
- **Gradient Coefficient, $k_{i}$:** Dictates the energetic cost of spatial variations in $\phi_i$.

In essence, the Ginzburg-Landau free energy captures the balance between local free energy, interactions between components, and the cost of creating interfaces between different phases. This balance dictates the system's behavior, including the nature and morphology of the phases during phase separation.
### **2.3 Effective Nonequilibrium Chemical Potential**
Given by:

$$ \mu_{i}^{neq}= \mu_{i}^{eq} + \sum_{j=1}^{N}\alpha_{ij}\phi_j  $$

This expresses the chemical potential of species `i` in the presence of nonreciprocal activity.
### Properties:

#### Equilibrium Phases:
In the absence of interspecies interactions, each species $i$ phase separates into bulk phases with densities $c_{i,1}$ and $c_{i,2}$, which are densities away from the interface.

#### Interspecies Interactions:
Interactions between different species are controlled by coefficients $ \chi_{ij}$ and $\chi^{'}_{ij}$.

#### Departure from Equilibrium:
For single-component systems, various factors can lead to departures from equilibrium. Some models introduce additional terms, while others introduce activity by breaking the fluctuation-dissipation relation.

# B. Nonreciprocal interactions in a binary mixture
For a binary mixture, the free energy can be written as
$$ F = \int d \mathbf{r} \left[ \sum_{i=1}^{2}(\phi_i-c_{i,1})^2(\phi_i-c_{i,2})^2 + (\chi_{ij}\phi_i\phi_j+\chi^{'}\phi_i^2\phi_j^2)+\sum_{i=1}^{2}\frac{k_{i}}{2}|\nabla_{i}|^2 \right] $$

which results in equilibrium chemical potentials
$$ \mu_{1}^{eq} =2(\phi_1-c_{1,1})(\phi_1-c_{2,2})(2\phi_1-c_{1,1}-c_{1,2})+\chi\phi_2+2\chi^{'}\phi_1\phi_2^2
$$
$$ \mu_{2}^{eq} =2(\phi_1-c_{2,1})(\phi_1-c_{2,2})(2\phi_1-c_{2,1}-c_{2,2})+\chi\phi_1+2\chi^{'}\phi_2\phi_1^2
$$
---
## Equilibrium Interactions
**Flory-Huggins Equation**



The Flory-Huggins free energy of mixing for a polymer solution can be expressed as:

$$ \Delta G_{mix} = k_B T \left[ \phi_1 \ln(\phi_1) + \phi_2 \ln(\phi_2) + \chi \phi_1 \phi_2 \right] $$

Where:
- $k_B$: Boltzmann constant.
- $T$: Absolute temperature.
- $\phi_1$ and $\phi_2$: Volume fractions of the solvent and the polymer, respectively.
- $\chi$: Flory-Huggins interaction parameter.


**Understanding the Interaction Parameter:**

At equilibrium, the nature of interaction between the two species is determined by the value of $ \chi $:

- $ \chi > 0 $: This denotes **repulsive** interactions between the species. An overlap or an increase in proximity between the species leads to an increase in the system's free energy, making them want to stay apart.

    1. **Miscible Phase:** If $\chi < 0.5$, the polymer and solvent are miscible across all compositions.
    2. **Critical Point:** At $\chi = 0.5$, a critical point emerges below which the polymer and solvent are still miscible.
    3. **Phase Separation:** When $\chi > 0.5$, phase separation is witnessed, leading to distinct regions of pure solvent and pure polymer.
  
- $ \chi < 0 $: This signifies **attractive** interactions. Here, the overlap or increased proximity decreases the system's free energy, causing the species to be drawn to one another.



---

## Nonreciprocal Nature of Interactions

The inclusion of the activity $ \alpha $ modifies the interaction between the species when they aren't at equilibrium:

1. When $ \chi > 0 $ (repulsive interactions):

   - If $ 0 < \alpha < \chi $, the interactions remain repulsive. However, species 1 is more strongly repelled by species 2 than the other way around.
   
   - If $ \alpha > \chi $, species 1 is repelled by species 2, but interestingly, species 2 is attracted to species 1.

2. For $ \chi < 0 $ (attractive interactions), a similar nonreciprocal behavior can be expected based on the relative values of $ \alpha $ and $ \chi $.

This nonreciprocity implies that in the presence of non-equilibrium factors (like activity), one species' response to the other is not symmetric. This can have profound implications for the dynamics, phase separation, and pattern formation in binary mixtures.


