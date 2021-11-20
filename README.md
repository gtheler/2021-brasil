---
title: |
 | A free and open source computational tool for solving
 | (nuclear-related) differential equations in the cloud
author: German (a.k.a. Jeremy) Theler
email: gtheler@seamplex.com
institute: |
 | International Nuclear Atlantic Conference
 | Round Table 4 ENFIR Best Estimate codes and methods
 | for Reactor Physics, Thermal Fluid Dynamics and Fuel Behavior
aspectratio: 169
lang: en-US
theme: default
innertheme: rectangles
fonttheme: professionalfonts
outertheme: number
colorlinks: true
sansfont: Carlito
monofont: DejaVuSansMono
header-includes: \include{syntax.tex}
...


# Why $\rightarrow$ How $\rightarrow$ What

   
\centering ![](sinek.jpg)

\centering <https://www.youtube.com/watch?v=u4ZoJKF_VuA>

# 

\centering ![](why.svg)

# IAEA 2D/3D PWR benchmark (1976)

:::::::::::::: {.columns}
::: {.column width="40%"}
![PARCS](purdue.png){width=90%}
:::

::: {.column width="60%"}
![milonga](quarter.svg){width=85%}
:::
::::::::::::::

# Vertical PHWR (Atucha)

:::::::::::::: {.columns}
::: {.column width="50%"}
\centering ![](rpv2d.png){width=70%}
:::

::: {.column width="50%"}
\centering ![](rpv3d.jpg){width=60%}
:::
::::::::::::::


# Fuel elements


:::::::::::::: {.columns}
::: {.column width="33%"}
![PWR](pwr1.png)
:::

::: {.column width="34%"}
![BWR](bwr1.png)
:::

::: {.column width="33%"}
![BWR](candu1.png)
:::
::::::::::::::


# Steady-state core-level neutronic calculations

:::::::::::::: {.columns}
::: {.column width="50%"}
\centering ![](cara.jpg){width=60%}
:::

::: {.column width="50%"}
\centering ![](celdascna1.svg){width=60%}
:::
::::::::::::::


:::::::::::::: {.columns}
::: {.column width="33%"}
![](cna1calc.png){width=80%}
:::

::: {.column width="34%"}
![](cna1rep.png){width=80%}
:::

::: {.column width="33%"}
![](pow.png){width=70%}
:::
::::::::::::::


# Transient emergency boron injection---CFD

\centering ![](cfd.png)


# Transient emergency boron injection---core-level neutronics

:::::::::::::: {.columns}
::: {.column width="50%"}
\centering ![](4x4-40.png){width=80%}
:::

::: {.column width="50%"}
\centering ![](boropce.png){width=80%}
:::
::::::::::::::


# Transient emergency boron injection---cell-level neutronics


\centering ![](gota.svg){width=70%}


\centering ![](4x4ref.svg){width=80%}


#

\centering ![](how.svg)


# A little bit of history---College (2004-2008) (v1)

 * Solve $\dot{\mathbf{x}} = F(\mathbf{x},t)$
    
    a. program an _ad-hoc_ numerical method
    b. use a standard numerical library in C or Python, or
    c. use a high-level system such as [Octave](https://www.gnu.org/software/octave/index), [Maxima](https://maxima.sourceforge.io/), etc.
    
. . .
    
 * Point reactor equations solved "graphically" with non-free software

   $$
   \begin{cases}
   \dot{\phi}(t) = \displaystyle \frac{\rho(t) - \beta}{\Lambda} \cdot \phi(t) + \sum_{i=1}^{N} \lambda_i \cdot c_i \\
   \dot{c}_i(t)  = \displaystyle \frac{\beta_i}{\Lambda} \cdot \phi(t) - \lambda_i \cdot c_i
   \end{cases}
   $$
   
. . .
   
 * I would rather write the equations in ASCII like

   ```
   phi_dot = (rho-Beta)/Lambda * phi + sum(lambda[i], c[i], i, 1, N)
   c_dot[i] = beta[i]/Lambda * phi - lambda[i]*c[i]
   ``` 

# A little bit of history---Nuclear industry (2008--2014)

. . .

\centering ![](FortranCardPROJ039.jpg)



# Spatial discretizations

:::::::::::::: {.columns}
::: {.column width="50%"}
\centering ![](dominio-continuo.svg){width=80%}
:::

. . .

::: {.column width="50%"}
\centering ![](dominio-continuo-estructurado.svg){width=80%}
:::
::::::::::::::


. . . 

:::::::::::::: {.columns}
::: {.column width="50%"}
\centering ![](dominio-estructurado.svg){width=80%}
:::


. . . 

::: {.column width="50%"}
\centering ![](dominio-no-estructurado.svg){width=80%}
:::
::::::::::::::

# wasora & milonga (v2)

:::::::::::::: {.columns}
::: {.column width="30%"}
\centering ![](wasora.svg){width=100%}

Wasora's an advanced suite for reactor analysis

\centering ![](vibora-blanca.svg){width=100%}
:::

::: {.column width="70%"}

 * Coupled unstructured fine-mesh neutronics and thermal-hydraulics methodology using open software (2018)
 * Open software one-step coupled neutronics and CFD thermalhydraulics calculation (2016)
 * <https://github.com/seamplex/milonga-2015-workshop>
 * Reactivity coefficient estimation by fuel temperature for Atucha II Nuclear Power Plant from neutron flux measurements (2014)
 * On the design basis of a new core-level neutronic code written from scratch (2014)
 * Neutron diffusion on unstructured grids: comparison between finite volumes and finite elements (2013)
 * Geometric optimization of nuclear reactor cores (2013)
 * Unstructured grids and the multigroup neutron diffusion equation (2013)

:::
::::::::::::::


# FeenoX (v3)

:::::::::::::: {.columns}
::: {.column width="50%"}

## Software Requirement Specifications
 
 * Industrial-level: open source for V&V
 * Extensible: free (as in freedom)
 * Cloud-first: programatically-defined
 * Arbitrarily scalable for large problems
 * Flexible
 * Web & mobile-based GUIs
 * QA
   * Reproducibility & traceability
   * Automated testing
   * Bug reporting & tracking
 * V & V

:::

. . .

::: {.column width="50%"}
## Software Design Specifications

 * GPLv3+
 * No-GUI script-friendly GNU/Linux binary
   ![](transfer.svg){width=90%}\ 
 * Scalability based on
   * UNIX (separation, composition, etc.)
   * PETSc/SLEPc (MPI)
   * Gmsh (Metis)
 * Flexibility shown in "what"
 * Web GUI: <https://www.caeplex.com>
 * Everything is Git-tracked
 * Regression testing `make check`
 * Github-hosted
 * V & V: TO DO (help appreciated)!
:::
::::::::::::::

\begin{center}
\url{https://www.seamplex.com/feenox}
\end{center}


# 

\centering  ![](what.svg)


# Point kinetics

# Inverse kinetics

# Xenon feedback + control

# Measuring reactivity coefficients

# 2d pwr

# bunny

# cube-sphere

# pescaditos

# two-squares





