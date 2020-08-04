# BT for robot

Behavior Tree example for ROS

# Build up environment

1. git clone the repo.
```
mkdir -p ~/ros1_bt_ws/src
cd ~/ros1_bt_ws/src
git clone https://github.com/Adlink-ROS/BT_ros1.git
```

2. Install dependencies
```
cd ~/ros1_bt_ws
rosdep install --from-paths src --ignore-src -r -y
```

3. Build
```
catkin_make
```

# Usage

The BT example (refer to [bt_robot_nav_interrupt.xml](bt_xml/bt_robot_nav_interrupt.xml)) will make Robot move between Goal_a and Goal_b.
If receiving `/interrupt_event`, which is `gohome`, then Robot will move to Goal_c.

* Open 1st terminal and run turtlebot3 world. (melodic environment)
```
roslaunch turtlebot3_gazebo turtlebot3_world.launch 

```
* Open 2nd terminal and run navigation. (melodic environment)
```
roslaunch turtlebot3_navigation turtlebot3_navigation.launch
```
* Open 3rd termainal and run BT. (melodic environment) 
```
rosrun bt_robot node _file:=$HOME/catkin_ws/src/bt_robot/bt_xml/bt_robot_nav.xml
```
* Open 4th try the terminal and pub interrupt event. (melodic environment)
```
rostopic pub /interrupt_event std_msgs/String "gohome"
```
