I'm going to use one of the Husky's and Turtlebot's tutorial together. 
This tutorial shows how to create a publisher for husky https://www.clearpathrobotics.com/assets/guides/ros/Creating%20publisher.html
This one shows how to subscribe for Turtlebot https://github.com/cagrikilic/huskyKinetic/blob/slave/tutorials/tutorialTurtlebotIndigo0.md
So I have a ros bag file, and it publishes
```
/husky_velocity_controller/odom   nav_msgs/Odometry
/odometry/filtered                nav_msgs/Odometry
```
They include geometry_msgs/Twist so I can get velocity information from them. 
Then I can use this velocity information in the code and drive husky.

I should fuse these two codes
## Husky Random Driver 
```
#include <ros/ros.h>
#include <geometry_msgs/Twist.h>
#include <stdlib.h>

int main(int argc, char **argv) {
//Initializes ROS, and sets up a node
ros::init(argc, argv, "random_husky_commands");
ros::NodeHandle nh;

//Ceates the publisher, and tells it to publish
//to the husky_velocity_controller/cmd_vel topic, with a queue size of 100
ros::Publisher pub=nh.advertise<geometry_msgs::Twist>("husky_velocity_controller/cmd_vel", 100);

//Sets up the random number generator
srand(time(0));

//Sets the loop to publish at a rate of 10Hz
ros::Rate rate(10);

  while(ros::ok()) {
    //Declares the message to be sent
    geometry_msgs::Twist msg;
    //Random x value between -2 and 2
    msg.linear.x=4*double(rand())/double(RAND_MAX)-2;
    //Random y value between -3 and 3
    msg.angular.z=6*double(rand())/double(RAND_MAX)-3;
    //Publish the message
    pub.publish(msg);

    //Delays until it is time to send another message
    rate.sleep();
    }
}
```
## Turtlebot Location Monitor
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
