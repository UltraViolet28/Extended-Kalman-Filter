# Extended Kalman Filter for 2D Robot Localization

EKF implementation for estimating the 2D pose (x, y, heading) of a wheeled robot from noisy odometry and range-bearing measurements to known landmarks.

## Overview

This project implements an Extended Kalman Filter to localize a robot in a 2D environment with a set of known landmark positions. The filter fuses wheel odometry (linear and angular velocity) with LIDAR-style range-and-bearing measurements. Because both the motion model and the measurement model are nonlinear, the EKF linearizes them at each timestep using Jacobians before applying the standard Kalman predict-correct cycle. This is a self-study implementation written to understand the mechanics of EKF-based localization.

## Methods / Approach

- **State representation:** `[x, y, θ]` — position and heading
- **Motion model:** differential-drive kinematics driven by linear velocity `v` and angular velocity `ω` (from odometry)
- **Measurement model:** range and bearing to fixed, known landmarks; nonlinear in state
- **Linearization:** Jacobians `F_k` (motion), `H_k` and `M_k` (measurement) computed analytically at each step
- **Noise models:** process noise `Q = diag(v_var, ω_var)`, measurement noise `R = diag(r_var, b_var)`; tuned to `v_var = ω_var = 0.08`, `r_var = b_var = 0.01`
- **Angle wrapping:** heading error wrapped to `[-π, π]` before covariance update
- **Libraries:** NumPy, Matplotlib

## Results

Trajectory plots (EKF estimate vs. ground truth for position and heading over time) are embedded as output cells in `Kalman_Filter.ipynb`. The filter tracks ground truth closely; residual error is larger during turns, as expected from the odometry noise model.

## How to Run

Dependencies:

```
pip install numpy matplotlib jupyter
```

The input dataset is loaded from pickle files that are not included in this repository. Open and run `Kalman_Filter.ipynb` with your own data in the expected format (odometry inputs and landmark measurements per timestep), or examine the notebook for the filter logic and embedded result plots.

## Context

Self-study implementation of EKF localization, 2022.
