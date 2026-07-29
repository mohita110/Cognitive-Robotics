# BeetleBot Motion Control Using ROS 2

## Overview

This project demonstrates the basic motion control of the BeetleBot mobile robot using ROS 2 Jazzy. The robot is controlled by publishing velocity commands (`Twist` messages) to the appropriate ROS 2 topics and by using keyboard teleoperation. The project also demonstrates robot arming/disarming through ROS 2 services.

## Objectives

- Connect to the BeetleBot using ROS 2.
- Arm and disarm the robot.
- Move the robot using ROS 2 topic commands.
- Control the robot using the `teleop_twist_keyboard` package.
- Verify robot status using ROS 2 topics and services.

---

## Software Requirements

- Ubuntu 24.04
- ROS 2 Jazzy
- BeetleBot (Lyra Platform)
- teleop_twist_keyboard package

---

## ROS 2 Commands

### 1. Arm the Robot

```bash
ros2 service call /lyra/arm std_srvs/srv/Trigger
```

### 2. Check Armed Status

```bash
ros2 topic echo /lyra/armed
```

### 3. Move the Robot Forward

```bash
ros2 topic pub --once /cmd_vel_nav geometry_msgs/msg/Twist \
"{linear: {x: 0.2, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}"
```

### 4. Stop the Robot

```bash
ros2 topic pub --once /cmd_vel_nav geometry_msgs/msg/Twist \
"{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}"
```

### 5. Disarm the Robot

```bash
ros2 service call /lyra/disarm std_srvs/srv/Trigger
```

---

## Keyboard Teleoperation

Launch the keyboard teleoperation node:

```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

### Keyboard Controls

| Key | Action |
|------|--------|
| i | Move Forward |
| , | Move Backward |
| j | Turn Left |
| l | Turn Right |
| u | Forward Left |
| o | Forward Right |
| m | Backward Left |
| . | Backward Right |
| k | Stop |
| q/z | Increase or decrease maximum speed |
| w/x | Increase or decrease linear speed |
| e/c | Increase or decrease angular speed |

---

## Demonstration

The demonstration video shows:

- Robot initialization
- Robot arming
- Robot movement using ROS 2 commands
- Robot movement using keyboard teleoperation
- Robot stopping
- Robot disarming

---

## Repository Structure

```
.
├── README.md
├── videos/
│   └── beetlebot_motion_demo.mp4
├── screenshots/
│   ├── arm_robot.png
│   ├── teleop.png
│   ├── cmd_vel.png
│   └── disarm_robot.png
```

---

## Technologies Used

- ROS 2 Jazzy
- Ubuntu 24.04
- Geometry Messages (`geometry_msgs/msg/Twist`)
- Standard ROS 2 Services (`std_srvs/srv/Trigger`)
- teleop_twist_keyboard

---

## Author

**Mohita Grover**

B.Tech CSE (AI & Robotics)

Vellore Institute of Technology, Chennai
