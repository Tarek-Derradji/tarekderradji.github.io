---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Explore my doctoral journey and research interests.

About my Ph.D. 
======

<i>Title</i>. Numerical study of free-border problem and wave-structure interaction.

<i>Field</i>. Applied Mathematics, Mathematical Physics.

<i>Keywords</i>. Discontinuous Galerkin, Finite-Volume subcell, Shallow-Water, wave-structure interactions, ALE approaches.

<i>Abstract</i>. The general modeling of water waves in an incompressible and irrotational fluid can be ideally obtained with the Euler equations with a free surface boundary condition. For the particular case of shallow water regime, it is often needed to work with simplified asymptotic models allowing to simplify the analysis and work at the required physical scales. Several depth-integrated asymptotic models, allowing to reduce the dimension of the problem, have been recently introduced , analyzed, numerically approximated and experimentally validated. Such models are nowadays used to solve coastal engineering problems related to wave propagation and transformations.

In these asymptotic models, the study of free-boundary problems and the introduction of floating structures has not received much attention and remains a challenge. On the theoretical side, a recent work allows to rigorously analyze a nonlinear formulation accounting for the wave–body problem relying on the  shallow-water equations,  through the decomposition of the physical domain of interest between a free-surface domain and a floating structure domain, and introducing coupling conditions between these two sub-domains. On the numerical side, very few dedicated studies may be found in the literature.
In a very recent Ph.D thesis and submitted papers, a new numerical strategy is introduced in the d = 1 configuration, relying on a DG-ALE method which is further stabilized by an a posteriori Finite-Volume sub-cell correction.

During the proposed Ph.D., in order to further study this modeling problem, we aim at:
1. Invest some new stabilization methods for the NSW equations relying on an a priori paradigm, in the one and  two-dimensional cases, which is of paramount importance in such equations with singularities,
2. Extend the previous strategy to the two dimensional case, both from the modeling and the numerical viewpoints.

Besides this, the original feature of the chosen approach lies in the use of Arbitrary Eulerian Lagrangian method (ALE) to handle the mesh displacement and deformation. In the frame of continuous mechanics, two points of view are generally used, namely the Eulerian and Lagrangian formalisms. In the Eulerian framework, the conservation laws governing the physical phenomenon under consideration are developed on a fixed referential, while in the Lagrangian formalism the referential is attached to the material. Thus, in the case of hydrodynamic problem, the mesh should thus move and get deformed as the fluid flows. The ALE methods lies in between. 
Depending on the progress, some applications to the study of floating wave-energy converters may be investigated too.

***

Research Topics
=====

<b>Shallow-Water equations</b>

The Shallow-Water equations are a collection of partial differential equations that describe the behavior of fluids in shallow areas such as rivers, lakes, and coastal areas. Mathematicians, engineers, and scientists are all interested to them because they provide a fundamental framework for understanding fluid dynamics in a wide range of practical applications. SW equations were developed in the mid-nineteenth century by mathematicians and physicists who wanted to understand the behavior of water waves, obtained by  deriving the full Navier-Stokes equations, which describe fluid motion in general. The fluid was simplified by assuming that it is incompressible and inviscid, and that its depth is much smaller than its horizontal extent. The main advantage of this model is its computation cost, allowing scientists to perform big-scale simulations in real time.

<b>High-order discontinuous Galerkin schemes</b>

The discontinuous Galerkin (DG) method is a numerical scheme for solving partial differential equations. It was first introduced by Reed and Hill in 1973, and has since become a popular method for solving a wide range of problems, from fluid dynamics to electromagnetics. The DG method is based on the Galerkin method, which involves approximating a solution to a PDE as a linear combination of basis functions. However, unlike the continuous Galerkin method, which uses continuous basis functions, the dG method uses discontinuous basis functions. This allows for a more flexible and accurate approximation of the solution, particularly in areas with high gradients or shocks.

One of the main interests of the DG method is its ability to handle complex geometries and domains with irregular boundaries. This is because the method is naturally suited to handling non-uniform meshes and allows for the use of unstructured grids. The dG method is also well-suited to handle problems with multiple scales, such as those found in fluid dynamics or electromagnetism.
Compared to other numerical methods, such as finite difference and finite element methods, the DG method has several advantages. For one, the DG method is more accurate and robust than other methods in areas with strong discontinuities or singularities. 
This is because it can accurately capture the solution in these areas, whereas other methods may require finer mesh resolutions or more complex formulations.

Another advantage of this method is its ability to handle conservation laws. The dG method naturally conserves mass, momentum, and energy, which is important for many applications, such as fluid dynamics and electromagnetism. In contrast, other methods may require additional stabilization techniques to enforce conservation.
  
<b>Finite-Volume subcell corrections</b>

While the DG method has several advantages over other numerical methods, such as the Finite-Volume (FV) method, it also has some drawbacks that make it less robust in certain scenarios. One of the main disadvantages of the dG method is its difficulty in handling strong shocks and discontinuities. This is because the method relies on discontinuous basis functions, which can lead to numerical oscillations and instability in the presence of too strong gradients. In contrast, the FV method uses piecewise constant reconstructions, which are better suited to capturing shocks and discontinuities.

Another drawback of the DG method is its computational expense. The dG method can be computationally expensive, particularly for high-order methods or complex geometries, due to the need for a large number of degrees of freedom and the cost of computing numerical fluxes at the element interfaces. In contrast, the FV method is generally more computationally efficient, particularly for lower-order methods and simpler geometries.
Additionally, the dG method requires careful treatment of numerical fluxes at the interfaces between elements to ensure accuracy and stability. This can be particularly challenging in complex geometries or in the presence of strong shocks or discontinuities. In contrast, the FV method typically relies on simple numerical fluxes that are easy to implement and more robust in these scenarios. 

Another challenging problem, focusing on the NSW equations, is the preservation of the set of admissible states at the discrete level, which is closely related to the issue of the occurrence and propagation of wet/dry fronts that may occur in dam-breaks, flood-waves, or run-up over coastal shores. As a result, while maintaining the water-height positivity at the discrete level is a minimal nonlinear stability requirement, this is clearly a difficult task when high-order polynomials are used within mesh elements and standard (non-stabilized) DG methods may produce negative values for the water-height H in the vicinity of dry areas. 
In general, robustness issues may be among the most significant remaining challenges for the use of high-order methods in realistic problems in many domains of application, and in recent years, several approaches have been proposed to stabilize high-order approximations. 

In my Master's Thesis & Ph.D., we focus on Finite-Volume subcell correction, introduced by François Vilar. The primary aim of this correction method is to maintain the high accuracy and precise subcell resolution of dG schemes. Therefore, an a posteriori correction will be used only when necessary at the subcell scale, while ensuring the conservation of the scheme. To achieve this, the DG scheme will be reformulated as a subcell FV scheme using the correct numerical flux, resulting in the dG reconstructed flux. This forms the basis of the limiter framework.

At each time step, a candidate solution is computed, and if it meets certain criteria (such as being positive and non-oscillating), the solution is accepted and the computation continues. If the solution is not admissible, the previous time step is returned to, and a local correction is made at the subcell scale. This is called a posteriori limitation. Each cell is divided into subcells, and if a subcell's solution is detected as problematic, a robust first-order or second-order TVD numerical flux is used on the subcell boundaries. If the subcell solution is admissible, the high-order reconstructed flux is used, retaining the dG scheme's accurate resolution and conservation properties. Only the solution inside troubled subcells and its first neighbors are recomputed, while the rest of the solution remains unchanged.
