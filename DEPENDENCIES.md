# Runtime Dependencies

This repository adds gesture input and safe command mapping to an existing Go1
hardware stack. It does not own or reproduce the Jetson camera environment or
the Unitree real-robot bridge.

## Robot Camera Stack

The authoritative setup is maintained in:

- <https://github.com/sriram-2502/go1_density_social_nav>
- <https://sriram-2502.github.io/go1_density_social_nav/>

Verified laboratory configuration:

- Unitree Go1
- ZED 2i stereo camera
- Jetson AGX Xavier
- ROS Noetic and Python 3
- JetPack 5.1.2-b104 / L4T R35.4.1
- ZED SDK 5.1.2

The Jetson camera node publishes:

| Topic | Type | Purpose |
|:--|:--|:--|
| `/video` | `sensor_msgs/Image` | Live robot-view image |
| `/camera_pose` | `geometry_msgs/PoseStamped` | ZED camera pose |
| `/detections` | `autoware_msgs/DetectedObjectArray` | Tracked objects |

## Unitree Bridge

The operator laptop uses the existing Unitree real-robot workspace. It must
provide `unitree_legged_msgs` and the high-level bridge that accepts
`unitree_legged_msgs/HighCmd` on `/high_cmd`.

Hardware motion must not be enabled until command limits, timeouts, stop
behavior, network configuration, and supervision procedures have been validated.

