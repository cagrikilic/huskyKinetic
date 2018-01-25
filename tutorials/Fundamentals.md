Navigation:
Estimate the position, orientation and velocity of a vehicle

Odometry: odos metron (route measure)
- The use of data from motion sensors (e.g wheel encoders) to estimate change in position in time.
- Example
  Robot has two wheels, 0.5ft wheel diameter, 3 ft wheel base, encoder has 88 counts per revolution,
  Travel time 5 sec.
  Right encoder traveled 1000 counts
  Left encoder traveled 700 counts
  1- Right encoder made (1000/88)=11.36 -> 11*pi=34.54 ft & .36*2*pi=2.26 ft
      D_R=34.54+2.26= 36.8 ft
      V_R=distance/time=36.8/5=7.36 ft/sec
  2- Left encoder made (700/88)=7.95
      D_L=21.98+5.97=27.95 ft
      V_L=27.95/5=5.59 ft/sec
  3- Total Distance -> D_tot= (D_L+D_R)/2 =32.375 ft
  4- Average velocity -> V_avg= 32.375/5=6.475 ft/seconds
  5- Since D_R>D_L, robot turned to the Left
  6- Average angle the robot traveled -> Theta = (D_R-D_L)/WheelBase
      Theta=(36.8-27.95)/3 =2.95 rad
  7- X=D_tot* sin(Theta)=32.375*sin(2.95)=6.16ft & Y=D_tot*cos(Theta)=32.375*cos(2.95)=31.78ft

IMU=RATEGYROSCOPE+ACCELEROMETER
Inertial measurement units (IMUs) typically contain three orthogonal rate-gyroscopes and three orthogonal accelerometers, measuring angular velocity and linear acceleration respectively. By processing signals from these devices it is possible to track the position and orientation of a device.Three gyros and three accelormeters are normally combined in an IMU. (e.g Honeywell HG1700)
An inertial measurement unit (IMU) contains a cluster of sensors: accelerometers (three or more, but usually three) and gyroscopes
(three or more, but usually three). These sensors are rigidly mounted to a common base to maintain the same relative orientation.
An IMU (giving f_ib_b::this means specific force of the body system(b) relative inertial space (IB) and w_ib_b) is sufficient to navigate relative to inertial space (no gravitation present) given initial values of Velocity, position and attitude.
  -- Integrating the sensed acceleration gives VELOCITY
  -- Second integration gives POSITION
  -- To integrate in the correct direction, ATTITUDE is needed. Attitude obtained by integrating the sensed ANGULAR VELOCITY

INS: The combination of an IMU and a computer running navigation equations is an INS.

INS:An inertial navigation system (INS) is a navigation aid that uses a computer, motion sensors (accelerometers), rotation sensors (gyroscopes) and occasionally magnetic sensors (magnetometers), to continuously calculate by dead reckoning the position, the orientation and the velocity (direction and speed of movement) of a moving object without the need for external references.

Inertial navigation systems are self-contained non-jammable, dead reckoning navigation systems
which provide dynamic information through direct measurements.
INS generally comprises gyroscopes(provide angular rate) and accelerometers(velocity rate). To
maintain an estimate of the position, velocity, and attitude rates of the vehicle in or on which the INS is carried.
(GPS for position, compass for angular orientation, and gyroscopes for angular rate)

INS
http://www.aerostudents.com/courses/avionics/InertialNavigationSystems.pdf
http://www.navlab.net/Publications/Introduction_to_Inertial_Navigation_and_Kalman_Filtering.pdf
https://www.cl.cam.ac.uk/techreports/UCAM-CL-TR-696.pdf
http://www.navlab.net/Publications/Introduction_to_Inertial_Navigation.pdf
http://www.navlab.net/Publications/The_Seven_Ways_to_Find_Heading.pdf





Inertial sensors: Always relative to inertial space
accelerometers,gyros(FOG, MEMS) are the most common ones.
Dead Reckoning: Relies on knowing where you started from plus some form of heading information and some estimate of speed.
Inertial Navigation: Relies on knowing your initial position, velocity and attitude and thereafter measuring your attitude rates and acceleration.

https://web.statler.wvu.edu/~irl/page34.html
https://web.statler.wvu.edu/~irl/page43.html
https://web.statler.wvu.edu/~irl/page26.html
https://web.statler.wvu.edu/~irl/page30.html
https://web.statler.wvu.edu/~irl/MAE493G_CpE493M_F2013_Lecture_2_Robot%20Design.pdf
https://web.statler.wvu.edu/~irl/Lab03_Calibration.pdf
https://www.novatel.com/products/span-gnss-inertial-systems/span-combined-systems/span-cpt/#overview
http://wiki.ros.org/hector_gazebo_plugins
http://wiki.ros.org/ethzasl_sensor_fusion
http://www.clearpathrobotics.com/assets/guides/ros/Creating%20subscriber.html#writing-the-subscriber
http://wiki.ros.org/husky_control/Tutorials/Interfacing%20with%20Husky
http://wiki.ros.org/husky_base
