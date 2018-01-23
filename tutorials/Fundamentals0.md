Navigation:
Estimate the position, orientation and velocity of a vehicle.

Sensing:(physical)
Performing measurements and collecting data

Perception:(mental)
Organization,identification, interpretation of sensory information to represent and understand the environment.

Wheel encoder
Track how far each wheel of a robot has traveled. This is by done tracking robot's wheel velocity. This velocity measurement can be used to estimate the robot relative position and heading angle

Inertial Measurement Unit (IMU)
Electronic device include a combination of 3 axis accelerometer and gyroscopes, sometimes magnetometers

Strap Down Inertial navigation
The inertial sensors are mounted rigidly onto the vehicle body. More computational, navigation equations are nonlinear.

Dead reckoning
The process of estimating one's current position based on a previously determined position and advancing that position based upon known or estimated speeds over elapsed time, and course (e.g inertial or encoder navigation)

1D Dead reckoning (random walk, unbounded cumulative errors)
Translation: P= integral(V,t)=double integral(a,t) :: wheel encoder for V, accelerometer for a
Rotation:    Psi=integral(r,t), angular rate, r, can be measured with a rate gyro

2D Strap Down Inertial Navigation
Five staties to estimate: (x,y,v_x,v_y, psi)
1- Yaw rate, heading,(psi) can be estimated yaw rate gyro measurement
2- Rotate the accelerometer measurements from the body frame to inertial frame
3- straight integration of acceleration to get the robot position in the inertial frame

% discretized velocity model (dead reckoning only)
% datain/dataout format: [time xpos ypos heading]
function [dataout] = VelModelUpdate(datain, Ts, vel_r, vel_l)
    Vs = (vel_r + vel_l ) / 2; % true velocity
    omega = (vel_r - vel_l ) / .263; % 0.263 is the wheel track (in meters)
    dataout=[ (datain(1)+Ts), 0, 0, 0];
    dataout(4) = datain(4) + omega*Ts; % get theta from last update / no change
    dataout(2) = datain(2) + Ts * Vs * cos( dataout(4) ); % new xpos
    dataout(3) = datain(3) + Ts * Vs * sin( dataout(4) ); % new ypos

GPS/INS Sensor Fusion

GPS provides a statistically unbiased solution but could jump (HIGH FREQUENCY jump) randomly around the true position
INS provides a smooth solution (through the integration process) but will drift over the time (LOW FREQUENCY error);

Working together, the GPS/INS sensor fusion algorithm will smooth out the GPS jumps and stop the INS drift.

Using strap-down inertial navigation equations for prediction;
(pg16 https://web.statler.wvu.edu/~irl/MAE493G_CpE493M_F2013_Lecture_9_Kinematics_Navigation.pdf)

Input vector u will include all inertial measurements:: u=[a_x_b,a_y_b,a_z_b, p, q, r]^t
The update will be based on the GPS measurements of the first six states:: y=[x,y,z,v_x,v_y,v_z]^t

We don’t have a direct measurement of the three Euler angle states, but that’s not a problem.

These three angles have showed up in the velocity prediction equations so the update with the velocity measurement will also provide
constraints on what the values of φ, θ, ψ can take.

1-Smooth out noisy GPS measurements
2-Provide estimates of attitude angles that were not measured directly!
