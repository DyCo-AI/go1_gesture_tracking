# Gesture Control

ROS Noetic C++ package for converting validated gesture intent into bounded
`unitree_legged_msgs/HighCmd` messages.

This package owns command timeouts, limits, stop precedence, and hardware arming.
Classifier output must never bypass this control boundary.

