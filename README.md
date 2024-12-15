## Robot Package Template

This is a GitHub template. You can make your own copy by clicking the green "Use this template" button.

It is recommended that you keep the repo/package name the same, but if you do change it, ensure you do a "Find all" using your IDE (or the built-in GitHub IDE by hitting the `.` key) and rename all instances of `articubot_one` to whatever your project's name is.

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).

I add the collision beside the visual to have a different view in the robot 

source install/setup.bash : 
source ~/dev_ws/install/setup.bash :
source /opt/ros/humble/setup.bash

ros2 launch articubot_one rsp.launch.py : launching that file where articubot_one is whatever you called your package

colcon build --symlink-install : building your workspace

rviz2 : open rviz2 to view the simulation of the robot
rviz2 -d src/articubot_one/config/view_bot.rviz : view with the current file 

ros2 run joint_state_publisher_gui joint_state_publisher_gui :  to resolve the problem that the wheels aren't displayed correctly and see the wheels visualised

ros2 launch articubot_one rsp.launch.py use_sim_time:=true : launch robot_state_publisher with sim time using the following command
ros2 launch gazebo_ros gazebo.launch.py : running Gazebo using the launch file provided by the gazebo_ros package
ros2 run gazebo_ros spawn_entity.py -topic robot_description -entity articubot_one : spawning the robot using the spawn script provided by gazebo_ros

ros2 launch articubot_one launch_sim.launch.py : run with gazebo
ros2 launch articubot_one launch_sim.launch.py world:=./src/articubot_one/worlds/obstacles.world : run robot with the current world

ros2 run teleop_twist_keyboard teleop_twist_keyboard : using tool called teleop_twist_keybroad ( can changed by using joystick with teleop_twist_joy -- teleop_node and joy -- joy_node )
ros2 run rqt_image_view rqt_image_view : viewing the result of the camera throught out this tool

ros2 topic echo /cmd_vel : checking the speeds on the /cmd_vel topic (with linear and angular)

ros2 control list_hardware_interfaces : seeing our hardware interfaces
ros2 control list_controllers : listing controllers

ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped : slightly

ros2 run controller_manager spawner diff_cont : interfacing with two or more wheels or motors, adjusting the speed or movement of the robot
ros2 run controller_manager spawner joint_broad : controlling and publishing the joint positions, velocities or efforts of a robot's joints
