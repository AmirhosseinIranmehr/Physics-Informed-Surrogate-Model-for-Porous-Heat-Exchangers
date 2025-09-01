# Physics-Informed-Surrogate-Model-for-Porous-Heat-Exchangers
The physics-informed surrogate model for lattice heat exchanger design is trained on CFD data to predict pressure drop, velocity, surface area, and mass. This enables rapid inverse design to maximize performance under constraints. The novel approach blends ML with fluid physics and is applicable to heat transfer, aerospace, and energy systems.

<img width="4403" height="2104" alt="Surrogate Model Framework" src="https://github.com/user-attachments/assets/cee5e462-60a4-4a5b-9ca0-3e896c7f2104" />


# Accelerating Heat Exchanger Design with Physics-Based Surrogate Modeling
This repository contains  the nTop + ASME IDETC-CIE Student Hackathon, where we developed a physics-informed surrogate model to predict and optimize the performance of a parameterized heat exchanger without relying on computationally expensive CFD runs.

# Problem Statement
Traditional design optimization for complex fluid-thermal systems, such as lattice-based heat exchangers, requires iterative geometry generation and full CFD simulations, both of which are computationally expensive. In this work we tried to Train a surrogate physics model capable of accurately predicting:

**1. Pressure Drop (Pa)**

**2. Average Flow Velocity (mm/s)**

**3. Core Surface Area (mm²)**

**4. Mass (g)**

**5. Reynolds Number**

*Eventually, we need to perform inverse design to maximize surface area while satisfying constraints on mass, pressure drop, and average velocity.*

# Physics-Based Approach
Instead of using a black-box ML model, the surrogate model was grounded in CFD-derived simulation data from a full factorial experiment design of a parameterized lattice cell geometry.

Inputs:

**1. Cell Size X (mm)**

**2. Cell Size Y/Z (mm)**

**3. Inlet Flow Velocity (mm/s)**

**Outputs: CFD-computed mass properties & flow metrics.**

The physics basis ensures that predictions respect governing fluid mechanics relationships, enabling trustworthy design decisions. By embedding physical relationships captured in CFD into the ML model’s training set, the surrogate retains high fidelity to the original physics while reducing evaluation times from minutes/hours to milliseconds. 

# Key Features
**Exploratory Data Analysis (EDA)**
1. Performed comprehensive EDA to examine feature correlations, distributions, and trends in CFD-derived outputs.
2. Identified physically meaningful relationships between cell sizes, inlet velocity, and thermal–fluid outputs.
3. Used pair plots, correlation heatmaps, and scatter matrices to visualize dependencies.
4. Detected nonlinearities and parameter interactions to inform model selection.
5. Verified dimensional consistency and ranges of all variables to ensure physical realism.
<img width="3570" height="2369" alt="tradeoff-plots" src="https://github.com/user-attachments/assets/fdb203ab-aa1c-4827-bfae-551549442462" />
<img width="1766" height="1182" alt="Mass-avg velocity feasible" src="https://github.com/user-attachments/assets/a25d3037-16d6-4ff1-a6c0-49feb9ce7674" />
<img width="1823" height="1186" alt="avg-pressuredrop feasible" src="https://github.com/user-attachments/assets/d182db38-c71a-409b-9980-5cafa7422936" />
<img width="1807" height="1173" alt="output" src="https://github.com/user-attachments/assets/149ad2d6-d335-4fd9-8789-56feed8271f2" />

**Surrogate Model Training**
1. Developed physics-informed regression models trained on high-fidelity CFD data.
2. Designed a reproducible training pipeline with preprocessing, scaling, and feature engineering.
3. Integrated k-fold cross-validation before final training to ensure robust performance estimation and reduce overfitting risk.

**Model Selection and Comparison**
1. Implemented multiple regression models (e.g., Random Forest, Gradient Boosting, Polynomial Regression, and Neural Networks).
2. Compared performance metrics (RMSE, R²) for each predicted quantity across models.
3. Selected the best-performing architecture for final deployment based on both **accuracy** and **computational efficiency**.
<img width="3052" height="2547" alt="Hist Residualas" src="https://github.com/user-attachments/assets/d83c2144-91b5-433c-ab05-1d28fddbb0ae" />
<img width="2829" height="2553" alt="Hist Results" src="https://github.com/user-attachments/assets/3b260e84-bbcf-4f1b-80cd-bb363bb9c858" />
<img width="2070" height="1020" alt="Hist parameters importance" src="https://github.com/user-attachments/assets/7fedd7bc-83dd-437d-bd79-3732711126fe" />

**Multi-Objective Optimization**
1. Applied inverse design to maximize core surface area while satisfying constraints on mass, average velocity, and pressure drop.
2. Utilized the trained surrogate for rapid parameter sweeps, enabling millisecond-level evaluations instead of lengthy CFD runs.
3. Demonstrated optimal designs by mapping feasible regions in the parameter space.

**Physics-Based Understanding**
1. Grounded the surrogate model in physical constraints learned from CFD simulations.
2. Ensured that predictions respect fundamental fluid mechanics principles, improving trust and interpretability.
3. Expanded the domain knowledge of the problem by data agumentation (125 to 890) by considering the features importance and physics-based corelations.

# Code Descriptions
Use the expeanded data in the repository for the code analysis. 
Run the notebook and the best model will be chosen between all models (e.g., Gradient Boosting) as "best_model". This would be further utilized to extract optimal design and perform the invers-design process. 
At the last block, you will be asked to add your inputs (X Cell-YZ Cell- Inlet Velociy), accordingly; based on the best model predcitions the results for comparison with nTop will be given. This would ensure the practibility of the model across different ranges of parameters and un-seen data.

# Applications
The methodology extends beyond this challenge to any complex engineering system where:
1. High-fidelity simulations are expensive.
2. Rapid design iteration is needed.
3. Physical interpretability is critical for trust in predictions.
