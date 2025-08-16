# Physics-Informed-Surrogate-Model-for-Porous-Heat-Exchangers
The physics-informed surrogate model for lattice heat exchanger design is trained on CFD data to predict pressure drop, velocity, surface area, and mass. This enables rapid inverse design to maximize performance under constraints. The novel approach blends ML with fluid physics and is applicable to heat transfer, aerospace, and energy systems.


# Accelerating Heat Exchanger Design with Physics-Based Surrogate Modeling

This repository contains  the nTop + ASME IDETC-CIE Student Hackathon, where we developed a physics-informed surrogate model to predict and optimize the performance of a parameterized heat exchanger without relying on computationally expensive CFD runs.

# Problem Statement

Traditional design optimization for complex fluid-thermal systems, such as lattice-based heat exchangers, requires iterative geometry generation and full CFD simulations—both of which are computationally expensive.
In this work we tried to Train a surrogate physics model capable of accurately predicting:

**1. Pressure Drop (Pa)**

**2. Average Flow Velocity (mm/s)**

**3. Core Surface Area (mm²)**

**4. Mass (g)**

**5. Reynolds Number**

Eventually, we need to perform inverse design to maximize surface area while satisfying constraints on mass, pressure drop, and average velocity.

# Physics-Based Approach

Instead of using a black-box ML model, the surrogate model was grounded in CFD-derived simulation data from a full factorial experiment design of a parameterized lattice cell geometry.

Inputs:

**1. Cell Size X (mm)**

**2. Cell Size Y/Z (mm)**

**3. Inlet Flow Velocity (mm/s)**

**Outputs: CFD-computed mass properties & flow metrics.**

The physics basis ensures that predictions respect governing fluid mechanics relationships, enabling trustworthy design decisions. By embedding physical relationships captured in CFD into the ML model’s training set, the surrogate retains high fidelity to the original physics while reducing evaluation times from minutes/hours to milliseconds. 

# Key Features
**Exploratory Data Analysis (EDA)**: Perform comprehsnive EDA to determine the features correlations, distrubtions, and patterns to augmentation of the data with better physics-based understanding. 

**Surrogate Model Training**: Built on simulation data to reflect fluid and thermal physics.

**Multi-Objective Optimization**: Inverse design to meet constraints while maximizing thermal performance.


# Applications

The methodology extends beyond this challenge to any complex engineering system where:

High-fidelity simulations are expensive.

Rapid design iteration is needed.

Physical interpretability is critical for trust in predictions.
