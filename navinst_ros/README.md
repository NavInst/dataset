# navinst_ros

`navinst_ros` is a ROS package that provides a collection of custom message definitions specifically designed for working with NavINST dataset. The messages are specifically required to deal with the  post-processed reference solution, indoor reference solution, OBD2 data, and radar data. 

Installing these custom messages is crucial for enabling seamless communication and data handling within ROS nodes that process these specific data types.

## Table of Contents
- [Instructions](#instructions)
- [Custom Messages](#custom-messages)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Instructions

To install and use the `navinst_ros` package, follow these steps:

1. **Copy the Package**: Assuming you have already cloned the main repository, copy the `navinst_ros` folder into the `src` directory of your catkin workspace:
     ```bash
     cp -r /path/to/navinst_ros ~/catkin_ws/src/
     ```

2. **Build the Package**: After copying the package, navigate back to your catkin workspace root directory and build the package using `catkin_make`:
     ```bash
     cd ~/catkin_ws
     catkin_make
     ```

3. **Source Your Workspace**: Once the build is complete, ensure you source your workspace to make the custom messages available for use:
     ```bash
     source devel/setup.bash
     ```

## Custom Messages
The `navinst_ros` package includes the following custom message types:

#### Post-Processed Urban Reference Solution:
- `INSPVA.msg`: Provides post-processed reference data, including position, velocity, and attitude information.
- `INSPVAX.msg`: An extended version of `INSPVA` with additional fields.
- Supporting Messages:
    - `Oem7Header.msg`
    - `InertialSolutionStatus.msg`
    - `INSExtendedSolutionStatus.msg`
    - `PositionOrVelocityType.msg`

#### Indoor Reference Solution

- `PoseWithEuler.msg`: A custom pose message that includes position information (x, y, z) combined with Euler angles for orientation.
- `EulerAngles.msg`: Represents orientation in terms of the Euler angles (roll, pitch, yaw).

#### OBD2 Data

- `ObdMeasurmentStamped.msg`: Time-stamped OBD2 measurement data such as speed, RPM, and Mass Air Flow.

#### Radar Data

- `radar_data.msg`: A custom message designed for 1D Doppler radar sensor data.
- Supporting Messages:
    - `fft.msg`
    - `raw.msg`



## Usage
Once installed, you can use these custom messages in your ROS nodes just like any other ROS message type. For example:
```bash
import rospy
from navinst_ros.msg import INSPVA

def callback(data):
    rospy.loginfo(f"Received data: {data}")

rospy.init_node('test_node', anonymous=True)
rospy.Subscriber('/novatel/reference/postprocessed/inspva', INSPVA, callback)
rospy.spin()
```
