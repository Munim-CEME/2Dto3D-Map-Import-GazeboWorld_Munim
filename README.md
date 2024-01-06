# 2D-to-3DMap-Import-to-GazeboWorld
Importing a pre-exisitng map created through RP 2D Lidar using Hector Slam into a Gazebo world and RVIZ for visualization with 4-wheel robot. This project is a continuation of the last project, referred in [this](https://github.com/SyedKirmani12/4WheelDrive_Gazebo_using_ROS) repo.
## Pre-requisites
Make sure that you have a pre-existing map present in the form of a png file, which would create a map topic to publish to the "map2gazebo" process and export the map in Gazebo as a 3D mesh.In our case, we had mapped a certain area using RP 2D LIDAR and rplidar_ros package. The robot body description folder would also be rquired to be present inside catkin workspace. PLease review the repo [here]([url](https://github.com/SyedKirmani12/4WheelDrive_Gazebo_using_ROS)) to clone.
## Steps to Simulation
The following steps are necessary for executing a Gazebo world containing your map.
1. Download the hector_slam package package into the catkin workspace's src folder. This package has to be downloaded(Download and Documentation on hector slam package for ros can be found [here]([url](http://wiki.ros.org/hector_slam))
2. Move your pre-existing map inside the maps folder
3. Make sure that map2gazebo folder is also available in src folder (IMPORTANT NOTE:  map2Gazebo packags has not been created on my end , and was taken from [this](https://github.com/shilohc/map2gazebo) repo.)
4. After this move to the directory - **~/catkin_ws/src/maps** and initalize roscore using **roscore** command
5. Now, in the same directory, run your map server using **rosrun map_server map_server.//yourmapname.yaml//**
6. Now launch the gazebo world. Before doing so, map2gazebo topic must be initialized by **roslaunch map2gazebo map2gazebo.launch**. Wait for the mesh to be created and exported and kill the node
7. Now, gazebo node can be launched by running **roslaunch map2gazebo gazebo_world.launch** to visualize the robot with map. Note that the launch file contains robot parameters as well as gazebo world parameters
8. This extrudes your map, and converts it into a 3D world. For further information on this package, refer to the link of repo given above
9. To view the robot in RVIZ along with the map, run the tutorial file from hector slam package using the **roslaunch hector_slam_launch tutorial.launch** command
10. If you wish to move the robot around in Gazebo and view the map changing dynamically, run the teleop node for motion 
 
