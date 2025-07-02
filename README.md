# RobotLearningFinal
This project implements a solution to the **Tower of Hanoi** problem using a **6-DOF OpenManipulator robot** with **ROS** communication.

The system integrates the following components:

- **Pick-and-place command generation via a Large Language Model (LLM)**  
- **Object detection and depth estimation using an Intel RealSense camera** to track pick and place locations  
- **Motion execution** through predefined Dynamic Movement Primitives (DMPs)

<p align="center">
  <img src="RL_OM_TOH.gif" alt="TOH" />
</p>

The robot receives high-level move instructions from the LLM, detects object poses via RealSense, and executes precise movements to solve the puzzle autonomously.

![Overview](Overview.png)

### Required ROS Packages

All necessary ROS packages are available at the following repository:

> 🔗 [https://github.com/shailjadav/ARL_25_noetic_packages.git](https://github.com/shailjadav/ARL_25_noetic_packages.git)

Make sure to clone the repository into your ROS workspace and build it before running the system:

```bash
cd ~/catkin_ws/src
git clone https://github.com/shailjadav/ARL_25_noetic_packages.git
cd ~/catkin_ws
catkin_make
source devel/setup.bash
```

### LLM
Tower of hanoi game solver with LLM(green part of the overview) and its scripts are located in the directory /LLM_TOH

## Task execution:
### 1. Simulation

To execute the task in simulation, follow the instructions provided in the `DMP_ToH/README.md`.

### 2. Real Robot Execution

To run the task on a real robot, follow these steps:

#### Step 1: Launch the Position Controller

```
roslaunch om_position_controller position_control.launch sim:=false use_rs:=true
```

### Step 2: Run the RealSense-Based Detection

```
cd src/Vision_ToH/
python3 rs_detect.py
```
This will detect the cube positions using a RealSense camera and publish their poses for pick-and-place execution.
### Step 3: Execution

Copy the files from `Code used on real robot` to your execution directory and execute them in the same way as in the simulation.


## Example Videos

We provided three example videos to showcase the functionality of our system.

The real execution of the base setup for tower of Hanoi is shown in `Real_Base_720p.mp4`, while another starting state is presented in `Real_Other_Starting.mp4`.
In `Simulation.mp4`, an example of the simulation is shown.
