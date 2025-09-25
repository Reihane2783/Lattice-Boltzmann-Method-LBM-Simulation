 Lattice Boltzmann Method (LBM) Simulation
This project implements the **Lattice Boltzmann Method (LBM)** to simulate fluid flow in complex geometries. LBM is a mesoscopic approach to computational fluid dynamics (CFD) that models fluid behavior using particle distribution functions on a discrete lattice.

 What Is LBM?
Unlike traditional CFD methods that solve macroscopic Navier-Stokes equations, LBM operates at a **mesoscopic level**, simulating the collective behavior of fictitious particles. It is especially powerful for handling:
- Complex boundaries  
- Porous media  
- Multiphase flows  
- Microfluidic systems  

The method consists of two main steps:
1. **Collision step:** Particles at each node interact and redistribute their velocities.
2. **Streaming step:** Particles propagate to neighboring nodes along discrete directions.

Core Concepts

- **Discrete lattice:** Typically 2D (D2Q9) or 3D (D3Q19) grid where each node holds a set of velocity distribution functions.
- **Distribution functions:** Represent the probability of particles moving in specific directions.
- **Macroscopic quantities:** Density and velocity are recovered by summing over distributions.

What This Simulation Does

In this project, I simulate the flow of a fluid (like water) through a domain containing an obstacle (like a rock in a river). The goal is to observe how the fluid navigates around the obstruction and analyze velocity patterns and pressure fields.

 
 Applications

- Fluid flow in porous media  
- Blood flow in capillaries  
- Airflow around buildings or vehicles  
- Educational tool for CFD and statistical physics

اگه خواستی می‌تونم برات کد پایه‌ای LBM بنویسم (مثلاً با شبکه D2Q9 و مانع دایره‌ای)، یا کمک کنم پروژه رو به صورت تعاملی در Jupyter Notebook اجرا کنی. آماده‌ای برای مرحله بعد؟
