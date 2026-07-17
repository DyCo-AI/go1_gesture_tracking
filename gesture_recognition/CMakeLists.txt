cmake_minimum_required(VERSION 3.0.2)
project(gesture_recognition)

find_package(catkin REQUIRED COMPONENTS
  rospy
  sensor_msgs
  std_msgs
)

catkin_python_setup()

catkin_package(
  CATKIN_DEPENDS rospy sensor_msgs std_msgs
)

install(DIRECTORY config models
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

