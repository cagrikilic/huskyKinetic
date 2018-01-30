

After installing the turtlebot in a new terminal
```
 roslaunch turtlebot_gazebo turtlebot_world.launch
```
And on another terminal
```
 roslaunch turtlebot_teleop keyboard_teleop.launch
```
We will create a new package but first we should create a workspace. In a new terminal
```
mkdir -p ~/catkin_ws_indigo/src
cd catkin_ws_indigo
catkin_make
```
then
```
source devel/setup.bash
```
Now we can create our package
```
cd src
catkin_create_pkg location_monitor rospy roscpp
```
Just in case bash the setup again
```
. ~/catkin_ws_indigo/devel/setup.bash
```
navigate to location_monitor
```
roscd location_monitor/
```
And then create a source
```
mkdir -p src
cd src/
```
Inside of the source create a cpp file
```
touch location_monitor.cpp
```
Edit the cpp file for subscribing the odometry data

```
#include "ros/ros.h"
#include "nav_msgs/Odometry.h"

void OdomCallback(const nav_msgs::Odometry::ConstPtr& msg) {
 double x = msg->pose.pose.position.x;
 double y = msg->pose.pose.position.y;
 ROS_INFO("x: %f, y: %f", x, y);
}

int main(int argc, char** argv) {
 ros::init(argc, argv, "location_monitor");
 ros::NodeHandle nh;
 ros::Subscriber sub = nh.subscribe("odom", 10, OdomCallback);
 ros::spin();
 return 0;
}
```
Navigate to location monitor and edit CMakeLists.txt inside of the location_monitor
We will add nav_msgs into this. Carefully find corresponding scripts and change/add as below
```
find_package(catkin REQUIRED COMPONENTS
  nav_msgs
  roscpp
  rospy
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES location_monitor
  CATKIN_DEPENDS
	nav_msgs
	roscpp
	rospy
#  DEPENDS system_lib
)

include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

add_executable(location_monitor_node src/location_monitor.cpp)

add_dependencies(location_monitor_node
   location_monitor_generate_messages_cpp)

## Specify libraries to link a library or executable target against
target_link_libraries(location_monitor_node
   ${catkin_LIBRARIES}
)
---
edit package.xml inside of the location_monitor
---
<buildtool_depend>catkin</buildtool_depend>
 <build_depend>nav_msgs</build_depend>
 <build_depend>roscpp</build_depend>
 <build_depend>rospy</build_depend>
 <exec_depend>nav_msgs</exec_depend>
 <exec_depend>roscpp</exec_depend>
 <exec_depend>rospy</exec_depend>
```
After that navigate to workspace
```
cd ..
cd ..
```
Then make the catkin again
```
catkin_make
```
Navigate to location monitor
```
roscd location_monitor
```
Then run the location_monitor node
```
rosrun location_monitor location_monitor_node
```
Or use this - http://wiki.ros.org/evarobot_odometry/Tutorials/indigo/Writing%20a%20Simple%20Subscriber%20for%20Odometry
