cmake_minimum_required(VERSION 3.0.2)
project(gesture_control)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  unitree_legged_msgs
)

catkin_package(
  INCLUDE_DIRS include
  CATKIN_DEPENDS roscpp std_msgs unitree_legged_msgs
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

install(DIRECTORY config
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

