## Robot Package Template

This is a GitHub template. You can make your own copy by clicking the green "Use this template" button.

It is recommended that you keep the repo/package name the same, but if you do change it, ensure you do a "Find all" using your IDE (or the built-in GitHub IDE by hitting the `.` key) and rename all instances of `articubot_one` to whatever your project's name is.

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).

I add the collision beside the visual to have a different view in the robot 

ros2 launch articubot_one rsp.launch.py : launching that file where articubot_one is whatever you called your package

colcon build --symlink-install : building your workspace

rviz2 : open rviz2 to view the simulation of the robot
rviz2 -d src/articubot_one/config/view_bot.rviz : view with the current file 

ros2 run joint_state_publisher_gui joint_state_publisher_gui :  to resolve the problem that the wheels aren't displayed correctly and see the wheels visualised
