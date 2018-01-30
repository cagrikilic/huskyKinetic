```
sudo apt-get install ros-indigo-turtlebot ros-indigo-turtlebot-apps ros-indigo-turtlebot-interactions ros-indigo-turtlebot-simulator ros-indigo-kobuki-ftdi ros-indigo-rocon-remocon ros-indigo-rocon-qt-library ros-indigo-ar-track-alvar-msgs
```
if you have a kobuki error it is more likely your Ubuntu was running a non-default version of python. 
Delete it and use the default version of python, which can solve the problem. For anaconda 
```
conda install anaconda-clean   # install the package anaconda clean
anaconda-clean --yes           # clean all anaconda related files and directories 
rm -rf ~/anaconda3             # removes the entire anaconda directory

rm -rf ~/.anaconda_backup
```
Then look what is your default python
```
which python
```
If you have a nodelet_plugins.xml error try this
1- Create a file named as nodelet_plugins.xml copy and paste below.
```
    <library path="lib/libslam_gmapping_nodelet">  
      <class name="SlamGMappingNodelet" type="SlamGMappingNodelet" base_class_type="nodelet::Nodelet">  
      <description>  
      Nodelet ROS wrapper for OpenSlam's Gmapping.  
      </description>  
      </class>  
    </library>  
 ```
 2- Then 
 ```
 sudo cp -R   "yourfilesite"/nodelet_plugins.xml  /opt/ros/indigo/share/gmapping/  
 ```
 
 in order to launch turtlebot
 ```
 roslaunch turtlebot_gazebo turtlebot_world.launch 
 ```
 
