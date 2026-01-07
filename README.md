# ts-milp-nilm-cplex
Two-stage MILP NILM implementation (docplex/CPLEX) + KL-DR-LR feature extraction (cvxpy) — PSUT project.
# TS-MILP NILM (CPLEX / docplex) + KL-DR-LR Feature Extraction

**Team:** Mariam Raed Yaqoub, Husam Sawaqed (PSUT)

## Overview
This project implements the two-step approach from the paper:
**“A Two-Stage Mixed Integer Programming Model for Distributionally Robust State-Based Non-Intrusive Load Monitoring (NILM)”**.

We follow the same workflow used in our implementation report:
1) **Feature Extraction (KL-DR-LR):** distributionally robust bounds per appliance state (cvxpy).
2) **Load Disaggregation (TS-MILP):** reconstruct appliance loads using a Two-Stage MILP model (docplex + IBM CPLEX).

## What we implemented
- KL-DR-LR convex optimization to estimate robust bounds (P_lower/P_upper) and ramp limits.
- TS-MILP objective: minimize reconstruction error + state switching penalty.
- Constraints: absolute error, feature bounds, ramping, and state transitions.

## Data / Experiment Setup
- Dataset: **AMPds**
- Appliances: Fridge (FRE), TV (TVE), Basement (BME)
- Time window: 2013-07-20 19:00–20:00 (1-minute resolution)

## Current Results (Synthetic Aggregate Validation)
We validated the formulation using a synthetic aggregate (sum of appliance ground truth).
- Solver time: ~0.62s (T=61)
- Aggregated accuracy: 100%
- Objective value: ~2.1144

> Note: Perfect total reconstruction does not always guarantee perfect appliance-level assignment when bounds overlap.

## Repo Structure
- `notebooks/` → code (.ipynb)
- `reports/` → PDF report
- `DATA.md` → dataset access instructions (no raw data included)

## How to run (local)
1) Install Python packages: `pip install -r requirements.txt`
2) Install and configure **IBM CPLEX**
3) Open `notebooks/TwoStage_NILM_code.ipynb` and run cells

## Credits
This is a group project by **Mariam Raed Yaqoub** and **Husam Sawaqed**.
