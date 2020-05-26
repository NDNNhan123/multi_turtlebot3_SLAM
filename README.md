# multi_turtlebot3_nav
turtlebot3 system
Installation Instructions

Prerequisites

    Ubuntu 18.04 LTS
    ROS - Melodic


Install all non-ROS prerequisite packages

```bash
sudo apt update && sudo apt install \
  git wget \
  python-rosdep \
  python-catkin-tools \
  python3-vcstool \
  python3-colcon-common-extensions \
  maven default-jdk   
```
  
Start a new ROS workspace, and pull in the necessary repositories
```bash
  mkdir -p ~/robotics_ws/src
  cd ~/robotics_ws
  wget https://raw.githubusercontent.com/NDNNhan123/turtlebot3_nav_fleet/master/get.repos
  vcs import src < get.repos
  ```

Install all the dependencies through rosdep
```bash
source /opt/ros/melodic/setup.bash
rosdep install --from-paths src --ignore-src -y -r \
  --skip-keys="rmf_fleet_msgs ament_lint_common rclpy rclcpp rosidl_default_generators ament_cmake builtin_interfaces"
```
 Build
 ```bash
 source /opt/ros/melodic/setup.bash
 catkin build
 ```
 
 Multi Turtlebot3 Simulation
 ```bash
   source ~/robotics_ws/devel/setup.bash
   export TURTLEBOT3_MODEL=burger; roslaunch ff_examples_ros1 multi_turtlebot3_ff.launch
 ```
   
 Run multiple goals for one robot:
  ```bash
    cd src/multi_turtlebot3_SLAM/simple_navigation_goals/scripts
    ls
    chmod +x move_base_seq 
    cd ~/robotics_ws
    
    
    roslaunch simple_navigation_goals gazebo_navigation_rviz.launch
    roslaunch simple_navigation_goals movebase_seq.launch
  ```
 Run multirobot mapping:
 
    roslaunch multi_turtlebots_mapping multi_turtlebot3.launch
    roslaunch multi_turtlebots_mapping multi_mapping.launch
