- to install a package

```
sudo apt-get install ros-kinetic-[package_name]
```
- ROS Nodes
 Process that perform computation using ROS client libraries such as roscpp and rospy.
 One node can commuicate with other nodes using ROS Topics, Services and parameters
 rosnode is used for to get information about the node.

 ```
rosnode info [node_name]: info about the node
rosnode kill [node_name]: kill running node
rosnode list: list the nodes
rosnode ping; check the connectivity

 ```
 - ROS messages
 ROS nodes communicate with each other by publishing messages to a topic. Messages are simple data structure containing field types.
 For example, to access std_msgs/msg/String.msg we can use std_msgs/String or if you use roscpp client, you need to include std_msgs/String.h
 ```
 rosmsg show [message]: shows the message description
 rosmsg list: list all Messages
 rosmsg md5 [message]; md5sum of a message
 rosmsg package [package_name]:list messages in a package
 ```
 - ROS Topics
 They used for exchanging messages for ROS Nodes. It can publish or subscribe. They are unidirectional.
 Ros nodes are not interested to know which node is publishing the topic or subscribing the topic.
 ```
 rostopic bw /topic: disp bandwidth used by the topic
 rostopic echo /topic: print the content of the topic
 rostopic find /message_type: find the topics using the given message type
 rostopic hz /topic: shows the publishing rate of the topic
 rostopic info /topic: print info of the active topic
 rostopic pub /topic message_type args: To publish a value to a topic with a message type
 rostopic type /topic: display the message type of the given topic

 ```

 - ROS Services
 When we need request/response kind of comm in ROS we have to use the ROS services. ROS topics can't do that kind of comm since they are unidirectional

 - ROS Bags
 The main application is data logging.
 ```
 rosbag record [topic_1] [topic_2] -o [bag_name]: record the given topics into a bag file. Record all topics -a argument.
 rosbag play [bag_name]: Play existing bag file.
 ```
 ROS Master:
 Example of usage, when publisher starts publishing `hello world` message in a particular topic, ROS maseter gets the detailes of the topic and the node, it will search whether any node is subscribing the same topic. When it finds it connect them.

 - ROS parameter
 A node can read, write, modify and delete parameter values from the parameter server. We can store parameters in a file and load them into the server. If the number of parameters is high, we can use YAML file to save it.
 ```
 /camera/name : 'nikon'
 /camera/fps : 30
 /camera/exposure: 1.2
 /camera/active: true
 ```
 The rosparam tool used to get and set the ROS parameter from the command line.
 ```
 rosparam set [parameter_name] [value]
 rosparam get [parameter_name]
 rosparam load [YAML file]
 ```
