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

/inverse_modeling/
    ├── forward_net.py      # Multi-head Attention Network
    ├── reverse_opt.py      # Gradient-based inverse solving
    └── seeds_manager.py    # Multi-seed global optimization

/magnetic_pose/
    ├── dipole_model.py     # Distributed dipole physics
    ├── pose_fit.py         # Least-squares optimization
    ├── sensor_loader.py    # 75-sensor ring calibration & IO
    └── trajectory_smooth.py

/anyskin/
    ├── anyskin_process.py  # Multiprocess data acquisition
    ├── heatmap.py          # Live Matplotlib heatmap
    └── viz.py              # Pygame vector-field viewer

/docs/
    └── SURP_poster.pdf     # Included for academic reference
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
Yit Xiaang Ztang
University of Minnesota – Twin Cities
