# Setting up Clearpath's Husky Repository for ROS Kinetic

KineticRos_Husky Setup
- Make sure you are using Ubuntu 16.04

### Prerequisites
- follow the installation process for ROS Kinetic
http://wiki.ros.org/kinetic/Installation/Ubuntu

open a terminal (Ctrl+Alt+T) and copy(Ctrl+C)-paste(Ctrl+Shift+V) 
```
sudo apt-get install ros-kinetic-controller-manager ros-kinetic-multimaster-launch ros-kinetic-lms1xx ros-kinetic-interactive-marker-twist-server ros-kinetic-twist-mux
```

**< or >**

Below are instructions to use `rosdep install` to install dependencies of a ROS workspace.

## Getting Started
open a new terminal

- In order to clone Husky common packages
```
mkdir -p husky_ws/src
cd husky_ws/src
git clone -b kinetic-devel https://github.com/husky/husky.git .
```
(adding a `.` at the end of `git clone -b kinetic-devel https://github.com/husky/husky.git` means it will put the repository's contents in that directory and does not create a new directory. **Note**: If you run `catkin_init_workspace` before `git clone _______ .` you will receive an error stating the directory must be empty)

Verify you are on the `kinetic-devel` branch and init the workspace:
```
git status
catkin_init_workspace
```

Now run catkin_make in the root directory of the workspace (`husky_ws`)
```
cd ..
catkin_make
```

If you receive errors due to missing packages (It may read "Could not find a package configuration file...") use rosdep install to install all dependencies. 

```
rosdep install --from-paths src --ignore-src -r -y
```

Follow [these instructions](http://wiki.ros.org/rosdep) if you do not have `rosdep` installed.

Run `catkin_make` again after `rosdep` finishes


Up to now it should look like that
![1stImage](https://github.com/cagrikilic/huskyKinetic/blob/master/img/sc1.png)
![2ndImage](https://github.com/cagrikilic/huskyKinetic/blob/master/img/sc2.png)

Finally, edit the serial port path used by the husky base launch file to connect to the husky base controller. In the file "~/husky_ws/src/husky_base/launch/base.launch", replace the line
```
<arg name="port" default="$(optenv HUSKY_PORT /dev/prolific)" />
```
with the following: --- **TODO - will change with a proper port value**
run
```
ls /dev/serial/by-path/
```
Then use the port0 one in the next value sentence
```
<arg name="port" value= "/dev/serial/by-path/pci-0000:00:14.0-usb-0:9:1.0-port0" />
```

# Running Simulation Husky in Gazebo

In order to open husky in gazebo, inside your `husky_ws`:

```
source devel/setup.bash
roslaunch husky_gazebo husky_empty_world.launch
```

Then open another terminal to view the husky model in rviz (in your `husky_ws`):
```
source devel/setup.bash
roslaunch husky_viz view_model.launch
```

If you do not want to keep sourcing the `devel/setup.bash` every time you open a new terminal then you can add it to the end of your `~/.bashrc` file, after the `source /opt/ros/kinetic/setup.bash`. For ex:

```
source /opt/ros/kinetic/setup.bash
source /path/to/husky_ws/devel/setup.bash
```







