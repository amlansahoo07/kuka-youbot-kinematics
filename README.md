# YouBot Kinematics and Trajectory Planning
This repository contains an implementation of kinematic computations and trajectory planning for the YouBot robot. The project is designed to solve forward and inverse kinematics, calculate Jacobians, detect singularities, and plan trajectories through checkpoints using predefined joint positions.

![Screenshot from 2025-01-13 23-50-28](https://github.com/user-attachments/assets/6aa54874-feda-447f-bafb-1bb95d6377cc)


## Project Overview
The key features of this project include:
- Forward and inverse kinematics computation for the Youbot arm.
- Shortest path calculation between multiple target positions using Cartesian coordinates.
- Smooth trajectory generation with intermediate transformations using cubic interpolation.
- Integration with ROS 2 for trajectory execution and visualization.
- Visualization of checkpoints using RViz markers.
  
## Features
- **Kinematic Models:** Uses a custom KUKA Youbot kinematics model to calculate joint positions.
- **Shortest Path Optimization:** Employs permutations to determine the most efficient checkpoint sequence.
- **Trajectory Interpolation:** Generates intermediate waypoints with decoupled rotation and translation transformations.
- **Inverse Kinematics Solver:** Computes joint positions iteratively for a smooth trajectory.
- **ROS 2 Integration:** Publishes trajectory messages for execution and visualization.
  
## How It Works
1. **Loading Targets:** The program retrieves predefined target positions in both joint and Cartesian space.
2. **Shortest Path Calculation:** It determines the most efficient sequence of checkpoints based on Cartesian distances.
3. **Intermediate Transformations:** For smooth transitions, the algorithm interpolates between checkpoints using matrix exponential and logarithmic operations.
4. **Joint Angle Computation:** The trajectory is converted to joint positions using an iterative inverse kinematics solver.
5. **Trajectory Execution:** The planned trajectory is published to the ROS 2 trajectory controller for execution.
   
## Prerequisites
- **ROS 2 (Humble):** Ensure a functional ROS 2 setup.
- **Python 3.8+**
- **Required Packages:** Install necessary Python libraries.
  ```bash
  pip install numpy scipy rclpy trajectory_msgs visualization_msgs
  ```
- **Kinematics Model:** Include the `YoubotKinematicStudent` and `TARGET_JOINT_POSITIONS` files.


## Visualization
- The planned trajectory and checkpoints can be visualized in RViz using markers. Checkpoints are displayed as colored spheres, with colors representing the order of traversal (blue to green).
![Screenshot from 2025-01-13 23-51-26](https://github.com/user-attachments/assets/54899ce1-8db0-4bb7-a161-bc3ff8fc40ac)

## Acknowledgments

- This project was developed as part of the assessment for the [COMP0246 - Modelling and Motion Planning](https://www.ucl.ac.uk/module-catalogue/modules/modelling-and-motion-planning-COMP0246) module at University College London. 
- It was a collaborative effort by myself, [@ziyaruso](), and [@lorenzouttini](https://github.com/lorenzouttini).
- Special thanks to the teaching team for providing guidance and resources throughout the project.

## License
[MIT License](LICENSE)
