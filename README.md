husky_customization
===================

Templates for user customization of Husky description (URDF) and Gazebo configuration.

 - husky_custom_description : Template for creating a custom URDF description Husky robot
 - husky_custom_gazebo : Template for creating a custom Gazebo simulation configuration

For Husky instructions and tutorials, please see http://wiki.ros.org/Robots/Husky

For this installation, local (user laptop for example) pre-requisites can be installed with:
```
rosdep install robotiq_modbus_tcp
sudo apt-get install ros-indigo-soem -y
sudo apt-get install ros-indigo-ur-modern-driver -y
sudo apt-get install ros-indigo-moveit-planners* -y
sudo apt-get install ros-indigo-moveit-ros-planning* -y
sudo apt-get install ros-indigo-moveit-ros-move-group -y
sudo apt-get install ros-indigo-moveit-ros-control-interface -y
```

On the system with a user interface (either the robot or laptop, user computer, etc) you will also need to install:
```
sudo apt-get install ros-indigo-moveit-visual-tools
sudo apt-get install ros-indigo-moveit-ros-visualization
```

To launch the planner on a local laptop, ensure ROS_IP (your machine IP) and the computer's IP (Husky IP) are exported properly (you may have to edit your /etc/hosts file):
```
export ROS_IP=192.168.131.X
export ROS_MASTER_URI=http://cpr-sssa01:11311
```

On the robot, the UR5 driver should be brought up manually, as the UR5 arm can be powered on and off separately from the rest of the robot:
```
roslaunch sssa01_moveit ur5.launch
```
Once the driver is up, the planner can be started on the robot, or on the laptop (as long as exported properly, etc) with:
```
roslaunch sssa01_moveit kaust02_planning_execution.launch
```

Once both of the above steps are done, the user interface may be launched on the user laptop with:
```
roslaunch sssa01_moveit moveit_rviz.launch
```

Be sure to try out different planners, as some are significantly faster and more efficient than others.

![](http://i.imgur.com/tzbjJ6M.png)

Notes:
The Robotiq gripper fingers cannot be accurately simulated, as they are not sensored. It is suggested to keep the gripper closed if movements near the UR arm (self intersection) are being done.
