# Tactile Intelligence Suite
Inverse Neural Modeling + Distributed-Dipole Magnetic Pose Estimation + AnySkin Integration

A full-stack computational framework for reconstructing physical properties, sensing deformation, and estimating 3D pose of soft linear magnets (MIMMS). This project integrates inverse neural modeling, magnetic sensor array processing, and soft-magnet shape estimation using a flexible distributed dipole model.

---

## Overview

This repository implements three major subsystems:

### 1. Inverse Neural Modeling for Soft MIMMS
Predict key physical parameters:
- Magnetic field strength (mt)
- Young’s Modulus (E)
- Unit length (L)
- Cross-section size (cs)

Features:
- Reverse optimization through gradient descent
- Multi-head attention forward neural network
- Multi-seed global searching
- Parameter clipping to enforce physical realism

The system iteratively adjusts (cs, E, L) such that the forward network's curvature prediction matches the target deformation coefficient \hat{a}. Refer to the SURP poster for the optimization flow and architecture.

---

### 2. Flexible Magnet 3D Pose Estimation
A 75-sensor ring array captures magnetic field vectors. A distributed dipole model reconstructs the magnet’s full 3D shape.

Key capabilities:
- Sensor calibration and baseline estimation
- Dipole-based magnetic forward simulation
- Least-squares optimization to match measured and predicted fields
- Smooth curve fitting for magnet trajectory
- Typical performance: < 3 mm position error, < 5° orientation error

Frames 120 and 228 provide examples of dipole alignment and pose reconstruction quality.

---

### 3. AnySkin Surface Deformation Sensing
Real-time magnetic-field-based tactile sensing.

Includes:
- Multiprocessing magnetic data streaming
- Real-time heatmap visualization
- Pygame vector-field rendering
- Baseline frame subtraction
- Integration-ready for GeoSight deformation replay

Heatmaps and vector renderings show force direction, magnitude, and Z-axis changes.

---

## Repository Structure

====================
```text

Reverse Neural Network Calculation/
|-- megnet_robot_traj/
|   |-- Inverse_Results/
|   |-- Sim_Magenet/
|   |-- __pycache__/
|   |-- dataset/
|   |-- model/
|   |-- results/
|   |-- tf/
|   |-- utils/
|   |-- cal_curve.py
|   |-- inverse_optimize.py
|   |-- main.py
|   |-- main_with_reverse.py
|   |-- quadratic_curve.png
|   |-- reverse_search.py
|   |-- test.py
|   `-- IROS_2025_Sim_of_MIMMs(2).pdf

SKIN/
|-- Demo_Video/
|-- Material/
|-- OldVersions/
|-- anyskin/
|-- AnySkin_Models_Model.stl
|-- AnySkin_Models_Model_new.stl
|-- Assembly1.iam
|-- Assembly2.iam
|-- Box.ipt
|-- Franka_pair.stl
|-- LEAP.stl
|-- MAG_AnySkin_Models_Model.stl
|-- Magne_Cover.ipt
|-- OnRobot.stl
|-- Product_Model.ipt
|-- Tri_Box.ipt
|-- xArm_pair.stl
`-- xArm_pair_thin.stl

Soft Linear Magnet Detection/
|-- Example_Figures/
|-- data_capture/
|-- result_figures/
|-- results_analysis/
|-- .gitignore
|-- README.md
|-- data_loader_online.py
|-- main_animation.py
|-- requirements.txt
|-- test.py
|-- visualize_estimated_pose_sequence.py
`-- window.py

README.md
Yixin Chen-SURP_Poster_Pre_in_CUHK.pdf
```
## Installation

    git clone https://github.com/USERNAME/Tactile-Intelligence-Suite
    cd Tactile-Intelligence-Suite
    pip install -r requirements.txt

---

## Quick Start

### Run inverse modeling

    python inverse_modeling/reverse_opt.py --target_a 0.12 --mt 0.34

### Run magnetic pose estimation

    python magnetic_pose/pose_fit.py --data data/frame_120.npy

### Launch AnySkin viewer

    python anyskin/heatmap.py

---

## Applications

- Medical robotic manipulation
- Soft robot deformation sensing
- Magnetic tracking systems
- Flexible actuator characterization
- Robot tactile intelligence

---

## Citation

    Y. Chen, “Towards Tactile Intelligence: Inverse Neural Modeling and Magnetic Field Sensing for MIMMS,”
    SURP Presentation, Chinese University of Hong Kong, 2025.

---

## Author
Yit Xiaang Ztang \(Yixin Chen 陳奕昕\)
University of Minnesota – Twin Cities
