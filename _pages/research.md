---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

About my Ph.D. 
======

<i>Title</i>. Numerical study of free-border problem and wave-structure interaction.

<i>Field</i>. Applied Mathematics, Mathematical Physics.

<i>Keywords</i>. Discontinuous Galerkin, Finite-Volume subcell, Shallow-Water, wave-structure interactions, ALE approaches.

<i>Abstract</i>. The complete description of the flow of an irrotational and incompressible free surface fluid can be theoretically obtained thanks to the free surface Euler equations. In practice, however, it is often necessary, in a “shallow water” flow regime, to work with asymptotic models in order to allow simulations at realistic scales. Physical models integrated according to the vertical dimension, which nevertheless allow a very precise asymptotic description of the flow, have thus recently been proposed, validated experimentally and implemented numerically. 
Such models are now tools used in coastal engineering to simulate wave propagation and transformations. 

In these asymptotic models, the resolution of free-boundary problems and the consideration of floating objects on the surface haven't been much studied and remain a challenge. On the theoretical level, a recent work made it possible to rigorously analyze a non-linear formulation taking into account the presence of an object floating in the fluid by breaking down the field of study into a part with a free surface and a part congested by the presence of the object, and explaining in a simple way the conditions of transmission between these subdomains. Numerically, very few studies have been proposed using this type of formulation. In a very recent thesis work (Ali Haidar's Ph.D.) and a submitted publication, a purely one-dimensional approach was introduced, based on a DG-ALE method, stabilized by a Finite-Volume type approach of sub-mesh a posteriori. In order to continue this work, within the framework of this thesis, we propose:
1. To study new stabilization strategies of the a priori type for shallow-water models, which are of particular importance for this type problems with singularities, first in the one-dimensional case, then in the two-dimensional case.
2. To extend the previous strategy to the two-dimensional case, which has not yet been done both theoretically (formulation of the boundary value problem with free boundary) and numerically.

The originality of our approach will also consist in coupling the previous method with an Arbitrary Lagrangian Eulerian (ALE) description of the flow to manage the displacement and the deformation of the mesh, thus making it possible to carry out the coupling with the object floating on the surface. Depending on the progress of the work, applications to the mechanical modeling of wave energy converters may be addressed.

***

Research Topics
=====

Shallow-Water equations
===
The Shallow-Water equations are a collection of partial differential equations that describe the behavior of fluids in shallow areas such as rivers, lakes, and coastal areas. Mathematicians, engineers, and scientists are all interested to them because they provide a fundamental framework for understanding fluid dynamics in a wide range of practical applications. SW equations were developed in the mid-nineteenth century by mathematicians and physicists who wanted to understand the behavior of water waves, obtained by  deriving the full Navier-Stokes equations, which describe fluid motion in general. The fluid was simplified by assuming that it is incompressible and inviscid, and that its depth is much smaller than its horizontal extent. The main advantage of this model is its computation cost, allowing scientists to perform big-scale simulations in real time.

High-order discontinuous Galerkin schemes
======
The discontinuous Galerkin (DG) method is a numerical scheme for solving partial differential equations. It was first introduced by Reed and Hill in 1973, and has since become a popular method for solving a wide range of problems, from fluid dynamics to electromagnetics. The DG method is based on the Galerkin method, which involves approximating a solution to a PDE as a linear combination of basis functions. However, unlike the continuous Galerkin method, which uses continuous basis functions, the dG method uses discontinuous basis functions. This allows for a more flexible and accurate approximation of the solution, particularly in areas with high gradients or shocks.

One of the main interests of the DG method is its ability to handle complex geometries and domains with irregular boundaries. This is because the method is naturally suited to handling non-uniform meshes and allows for the use of unstructured grids. The dG method is also well-suited to handle problems with multiple scales, such as those found in fluid dynamics or electromagnetism.
Compared to other numerical methods, such as finite difference and finite element methods, the DG method has several advantages. For one, the DG method is more accurate and robust than other methods in areas with strong discontinuities or singularities. 
This is because it can accurately capture the solution in these areas, whereas other methods may require finer mesh resolutions or more complex formulations.

Another advantage of this method is its ability to handle conservation laws. The dG method naturally conserves mass, momentum, and energy, which is important for many applications, such as fluid dynamics and electromagnetism. In contrast, other methods may require additional stabilization techniques to enforce conservation.
  
Finite-Volume subcell corrections
======
While the DG method has several advantages over other numerical methods, such as the Finite-Volume (FV) method, it also has some drawbacks that make it less robust in certain scenarios. One of the main disadvantages of the dG method is its difficulty in handling strong shocks and discontinuities. This is because the method relies on discontinuous basis functions, which can lead to numerical oscillations and instability in the presence of too strong gradients. In contrast, the FV method uses piecewise constant reconstructions, which are better suited to capturing shocks and discontinuities.

Another drawback of the DG method is its computational expense. The dG method can be computationally expensive, particularly for high-order methods or complex geometries, due to the need for a large number of degrees of freedom and the cost of computing numerical fluxes at the element interfaces. In contrast, the FV method is generally more computationally efficient, particularly for lower-order methods and simpler geometries.
Additionally, the dG method requires careful treatment of numerical fluxes at the interfaces between elements to ensure accuracy and stability. This can be particularly challenging in complex geometries or in the presence of strong shocks or discontinuities. In contrast, the FV method typically relies on simple numerical fluxes that are easy to implement and more robust in these scenarios. 

Another challenging problem, focusing on the NSW equations, is the preservation of the set of admissible states at the discrete level, which is closely related to the issue of the occurrence and propagation of wet/dry fronts that may occur in dam-breaks, flood-waves, or run-up over coastal shores. As a result, while maintaining the water-height positivity at the discrete level is a minimal nonlinear stability requirement, this is clearly a difficult task when high-order polynomials are used within mesh elements and standard (non-stabilized) DG methods may produce negative values for the water-height H in the vicinity of dry areas. 
In general, robustness issues may be among the most significant remaining challenges for the use of high-order methods in realistic problems in many domains of application, and in recent years, several approaches have been proposed to stabilize high-order approximations. 

In my Master's Thesis & Ph.D., we focus on Finite-Volume subcell correction, introduced by François Vilar. The primary aim of this correction method is to maintain the high accuracy and precise subcell resolution of dG schemes. Therefore, an a posteriori correction will be used only when necessary at the subcell scale, while ensuring the conservation of the scheme. To achieve this, the DG scheme will be reformulated as a subcell FV scheme using the correct numerical flux, resulting in the dG reconstructed flux. This forms the basis of the limiter framework.

At each time step, a candidate solution is computed, and if it meets certain criteria (such as being positive and non-oscillating), the solution is accepted and the computation continues. If the solution is not admissible, the previous time step is returned to, and a local correction is made at the subcell scale. This is called a posteriori limitation. Each cell is divided into subcells, and if a subcell's solution is detected as problematic, a robust first-order or second-order TVD numerical flux is used on the subcell boundaries. If the subcell solution is admissible, the high-order reconstructed flux is used, retaining the dG scheme's accurate resolution and conservation properties. Only the solution inside troubled subcells and its first neighbors are recomputed, while the rest of the solution remains unchanged.
