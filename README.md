# huskyKinetic
KineticRos_Husky Setup
Make sure you are using Ubuntu 16.04

### Prerequisites
- follow the installation process for ROS Kinetic
http://wiki.ros.org/kinetic/Installation/Ubuntu

open a terminal
```
sudo apt-get install ros-kinetic-controller-manager
sudo apt-get install ros-kinetic-multimaster-launch
sudo apt-get install ros-kinetic-lms1xx
sudo apt-get install ros-kinetic-interactive-marker-twist-server
sudo apt-get install ros-kinetic-twist-mux
```
## Getting Started
open a new terminal

- In order to clone Husky common packages
```
mkdir -p husky_ws/src
cd husky_ws/src
catkin_init_workspace
```
```
git clone -b kinetic-devel https://github.com/husky/husky.git
```
you should be in 

LoginName@DeviceName:~/husky_ws/src$ 
then 
```
cd husky/
git status
```
make sure you are "On branch kinetic-devel"

then come back to husky_ws (~/husky_ws$)




~/husky_ws/src/husky$ cd ..
~/husky_ws/src$ cd ..
```
catkin_make
```
then (LoginName@DeviceName)
```
source /home/LoginName/husky_ws/devel/setup.bash
```
in order to open husky in gazebo
```
roslaunch husky_gazebo husky_empty_world.launch
```
then open another terminal
this opens husky in rviz
```
roslaunch husky_viz view_model.launch
```



![My image](cagrikilic.github.com/huskyKinetic/sc1.png)




