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
  3- Total Distance -> D_tot= (D_L+D_R)/2 =33.375 ft
  4- Average velocity -> V_avg= 32.375/5=6.475 ft/seconds
  5- Since D_R>D_L, robot turned to the Left
  6- Average angle the robot traveled -> Theta = (D_R-D_L)/WheelBase
      Theta=(36.8-27.95)/3 =2.95 rad
  7- X=D_tot* sin(Theta)=32.375*sin(2.95)=6.16ft & Y=D_tot*cos(Theta)=32.375*cos(2.95)=31.78ft

INS:
Inertial navigation systems are self-contained non-jammable, dead reckoning navigation systems
which provide dynamic information through direct measurements.
INS generally comprises gyroscopes(provide angular rate) and accelerometers(velocity rate).
(GPS for position, compass for angular orientation, and gyroscopes for angular rate)
