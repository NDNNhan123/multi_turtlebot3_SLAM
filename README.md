# turtlebot3_nav_fleet
turtlebot3 fleet management system
Install all non-ROS prerequisite packages

sudo apt update && sudo apt install \
  git wget \
  python-rosdep \
  python-catkin-tools \
  python3-vcstool \
  python3-colcon-common-extensions \
  maven default-jdk 
  
Start a new ROS workspace, and pull in the necessary repositories

