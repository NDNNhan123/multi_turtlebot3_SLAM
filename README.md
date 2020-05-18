# turtlebot3_nav_fleet
turtlebot3 fleet management system
Installation Instructions

Prerequisites

    Ubuntu 18.04 LTS
    ROS - Melodic


Install all non-ROS prerequisite packages

sudo apt update && sudo apt install \
  git wget \
  python-rosdep \
  python-catkin-tools \
  python3-vcstool \
  python3-colcon-common-extensions \
  maven default-jdk 
  
Start a new ROS workspace, and pull in the necessary repositories
\\
  mkdir -p ~/client_ws/src\
  cd ~/client_ws\
  wget https://raw.githubusercontent.com/NDNNhan123/turtlebot3_nav_fleet/master/get.repos\
  vcs import src < get.repos\
  
Install all the dependencies through rosdep\\
\\
source /opt/ros/melodic/setup.bash\
rosdep install --from-paths src --ignore-src -y -r \
  --skip-keys="rmf_fleet_msgs ament_lint_common rclpy rclcpp rosidl_default_generators ament_cmake builtin_interfaces"
  
 Build\
 source /opt/ros/melodic/setup.bash\
 catkin build
 
 
 Multi Turtlebot3 Simulation\
   source ~/client_ws/devel/setup.bash
   export TURTLEBOT3_MODEL=burger; roslaunch ff_examples_ros1 multi_turtlebot3_ff.launch
   
   
 Run multiple goals for one robot:\
    roslaunch simple_navigation_goals gazebo_navigation_rviz.launch\
    roslaunch simple_navigation_goals movebase_seq.launch\
 
