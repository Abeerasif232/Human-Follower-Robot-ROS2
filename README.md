# Human Follower Robot Using Depth Camera

This project aims to develop a mobile robot capable of autonomously following a human using 
depth camera input, while also mapping its environment using LiDAR-based SLAM. The robot 
operates in a simulated ROS environment utilizing Gazebo and RViz. The human detection is 
handled through the MediaPipe library, which processes RGB-D data to extract the human's pose 
or centroid. Simultaneously, LiDAR data is used to construct a map of the environment using 
SLAM techniques. 

## Setup and Launch instructions
### 1. Prerequisites
* ROS 2 (Humble)

* Gazebo simulator and ROS 2 Gazebo packages

* Python3

* Dependencies (Mediapipe, opencv)



### 2. Creating a ROS2 Workspace and Simulation Setup
```bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
colcon build
source install/setup.bash
```

### 3. Clone the Project Package
```
cd ~/ros2_ws/src
###  Add the project Package (care_robot folder) in the 'src' folder  ###
```

### 4. Additional Folders 
Two Folders are given
* rviz_configs
* p_maps

Place these Folders in the 'home' directory.
Also change the path of the files of these folders in launch folder files.

### 5. Launch Instructions
#### Terminal 1:

```bash
cd ~/ros2_ws
colcon build
source install/setup.bash
cd src/care_robot/launch
ros2 launch maze3.launch.py
```
The Gazebo will open with the World, Robot and a Walking Actor in it.

#### Terminal 2:
```
cd ~/ros2_ws
colcon build
source install/setup.bash
cd src/care_robot/launch
ros2 launch amcl_launch.py
```
Now the RViz will open will the Robot and the Map.

#### Terminal 3:
```
cd ~/ros2_ws
colcon build
source install/setup.bash
ros2 run care_robot follower_node
```

Now a new window will open with the camera view of the robot. The robot will start detecting the human and follow him.

## Custom Node
* follower_node is a custom ROS 2 node developed as part of this project.


* It processes RGB and depth images from the robot’s depth camera to detect and follow a human using MediaPipe pose estimation.

* The node publishes navigation goals and velocity commands to enable the robot to follow the detected human autonomously.

## ROS 2 dependencies

* rclpy

* sensor_msgs

* geometry_msgs

* cv_bridge

* tf2_ros

* tf2_geometry_msgs

* launch

* launch_ros

* ament_index_python

