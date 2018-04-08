Title: Conservation laws - I (Continuum hypothesis) <!--In the name of Almighty-->
Date: 2017-10-22 18:32
Category: Blog


In ancient Greek philosophy, there were two opposite views about the nature of
physical phenomena, the discrete, and the continuum. Aristotle was the representative of the
continuous theory and Democritus of the atomistic one. Despite the quantitative challenge to the continuous nature of reality from Robert Boyle (1666), John Dalton (1808), Ludwig Boltzmann’s development of statistical mechanics during the late 19th century, the continuum hypothesis dominated science. However, at the start of the 20th century,  the fields of continuum mechanics and discrete particles dynamics evolved separately because of Einstein’s atomistic explanation for Brownian motion and
the scattering experiments of Rutherford.

Fluid  mechanics describes the  motion  of  fluids  and the related  phenomena  at
macroscopic scales, which assumes that  a fluid can be regarded as a continuous medium and
that their properties vary evenly throughout. Although, We all know very well that fluids are made up of molecules, which are in random motion, fluids are viewed at  macro-scale in which any small fluid element actually still contains many molecules. We can now define density or velocity at point in an average sense. That is as an average of velocities (or densities) of the molecules that pass through a small volume surrounding that point. The size of this small volume has to meet with certain criteria. It must be smaller than the physical dimensions of the region under consideration like the wing of an aircraft or the pipe in a hydraulic system. At the same time it must be sufficiently large to accommodate a large number of molecules to make any averaging meaningful. It seems that there is a lower limit to the size of this volume. 

For  example,  when we deal  with the  displacement  of  some  fluid  particle,  we
do mean  not  the displacement  of  an  individual  molecule,  instead we mean a displacement 
of  a  volume  element  containing  many molecules, though still regarded as a point
in space. This is the reason, we consider fluid mechanics as a branch of continuum mechanics,
which models matter from a macroscopic viewpoint without using the information that it is made out of molecules (microscopic viewpoint).  Continuum mechanics are governed by the laws of conservation which states that the total amount of energy, mass, and linear momentum in a closed
system remain constant, and that energy and mass can neither be created nor destroyed. They may change forms but cannot disappear.

The field of continuum mechanics includes
the study of solid mechanics, thermodynamics and fluid mechanics.
A key distinction between these fields is the choice of reference frame. As solids deform by small amounts, it is possible to follow a fixed collection of material as it evolves in time. This is termed the Lagrangian reference frame. For thermodynamics and fluid mechanics, the movement of the material is too great to keep track of a fixed collection and it is simpler to observe the flow past a reference volume
(called a control volume). This is termed the Eulerian reference frame.

Solid mechanics attempts to model the stress and strain of a material. The solid mechanics
concepts of stress were developed by Leonard Euler and the Bernoulli (James then John) with the
notion of the stress tensor finally formalised by Cauchy in 1823. The field of thermodynamics was developed during the industrial revolution to quantify the
interplay of heat and work. It provides continuum notions of temperature, pressure and entropy. The entire formulation of thermodynamics assumes a fluid at thermodynamic equilibrium which significantly limits the applicability of thermodynamics.

Continuum fluid dynamics models the flow of fluids away from hydrodynamic equilibrium,
typically for phenomena acting at larger time and length scales than required for thermodynamic
equilibrium. Continuum fluid dynamics models are governed by the Navier-Stokes equation, 
formulated independently by Claude-Louis Navier in 1822 and George Gabriel Stokes in 1845. Navier-Stokes equation represents a continuum implementation of Newton’s laws with a variety of closure assumptions, for example, the solids mechanics stress tensor is often
replaced by a scalar hydrodynamic pressure, a shear viscosity and, in some cases, a bulk viscosity.

Although, analytical solution of these non-linear partial differential equations is impossible for complex flow conditions, with the advent of computers, numerical solutions can be possible especially to study chaotic behaviour of fluid flows, a phenomenon known in fluid mechanics as turbulence.

The aforementioned continuity assumption breaks down and the continuum models fail to fully capture the
physics of the fluid flow, when the dimensions of the physical system become smaller. The degree of failure of continuity assumption can be expressed through
the Knudsen number

\begin{equation}
Kn = \dfrac{\lambda}{L}
\end{equation}

where $\lambda$ termed as mean free path is the average distance, any two molecules in the system travel to collide, $L$ is the characteristic size of the system of interest. Whenever there is impossible situation to apply the continuum mechanics to describe the physical phenomena of the fluid system, a molecular description is required  to provide the correct behaviour for the fluid. In the molecular description, Newton’s laws of motion to simulate
an apparently chaotic set of molecular trajectories, similar to the chaotic behaviour observed
in the continuum. This is the field of molecular dynamics (MD) which simulates nature as a collection of discrete atoms. Although MD is a very poweful tool, it experiences limitations primarily related with the
computational time, to model the inter-atomic forces, and to treat the most extreme scales, where quantum mechanics become important.

One of the ongoing research field is to develop the methodology for linking a local molecular description
to a large region simulated using a continuum description. This will include both computational
and theoretical development. The computational development will focus on a general purpose,
modern and robust computational tools to simulate a wide range of problems. The theoretical
emphasis will be on the development of a rigorous mathematical framework based on sound
physical principles. In doing this, some progress towards the goal of a unifying framework to link
and verify coupled models will be made.
