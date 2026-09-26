# 2D Lattice Boltzmann Method (LBM) Flow Simulation

A Python implementation of a two-dimensional **Lattice Boltzmann Method (LBM)** simulation for studying fluid flow through a channel, including flow around a circular obstacle.

The project implements the D2Q9 lattice model and provides visualization and post-processing of velocity, kinetic energy, and a simplified temperature-related quantity.

## Overview

This project simulates 2D fluid flow using the **Lattice Boltzmann Method** with:

- D2Q9 lattice model
- BGK single-relaxation-time collision operator
- Streaming step
- Inlet and outlet boundary conditions
- Circular obstacle / solid boundary
- Macroscopic density and velocity calculation
- Velocity-field visualization
- Velocity distribution analysis
- Kinetic-energy calculation
- Simplified temperature estimation
- 3D surface plots
- Time-dependent velocity plots
- GIF animation of the flow evolution

The simulation can also be run **without an obstacle** for comparison.

---

## Physical Model

The simulation uses the D2Q9 lattice:

\[
\mathbf{c}_i =
(0,0),
(1,0),
(0,1),
(-1,0),
(0,-1),
(1,1),
(-1,1),
(-1,-1),
(1,-1)
\]

with the standard D2Q9 lattice weights:

\[
w_0 = \frac{4}{9},
\qquad
w_{1-4} = \frac{1}{9},
\qquad
w_{5-8} = \frac{1}{36}.
\]

The equilibrium distribution is calculated using the standard low-Mach-number expansion:

\[
f_i^{eq}
=
w_i\rho
\left[
1
+3(\mathbf{c}_i\cdot\mathbf{u})
+\frac{9}{2}(\mathbf{c}_i\cdot\mathbf{u})^2
-\frac{3}{2}|\mathbf{u}|^2
\right].
\]

The BGK collision step is:

\[
f_i^*
=
(1-\omega)f_i
+
\omega f_i^{eq},
\]

where

\[
\omega = \frac{1}{\tau}.
\]

---

## Simulation Parameters

| Parameter | Value |
|---|---:|
| Grid size | 200 × 100 |
| Relaxation time, \(\tau\) | 0.8 |
| Collision frequency, \(\omega\) | 1.25 |
| Number of iterations | 500 |
| Obstacle radius | 10 lattice units |
| Obstacle position | (50, 50) |
| Maximum inlet velocity | 0.1 |
| Initial density | 1.0 |
| Initial temperature | 300 K |

---

## Simulation Workflow

The main simulation follows the standard LBM cycle:

1. Initialize the distribution functions and macroscopic variables.
2. Calculate the equilibrium distribution.
3. Perform the BGK collision step.
4. Stream the distribution functions.
5. Apply boundary conditions and obstacle bounce-back.
6. Calculate macroscopic density and velocity.
7. Store velocity fields for visualization.
8. Generate an animated GIF of the velocity evolution.

---

## Boundary Conditions

The model includes:

- Velocity boundary condition at the inlet
- Outlet boundary condition
- Bounce-back treatment at the circular obstacle
- No-obstacle configuration for comparison

The circular obstacle can be enabled through the obstacle mask:

```python
obstacle = np.fromfunction(
    lambda x, y:
    (x - obstacle_x) ** 2 + (y - obstacle_y) ** 2
    <= obstacle_radius ** 2,
    (nx, ny)
)
