Needs for Wheel Odometry
- CMakeLists.txt
autorally/autorally_core/src/WheelOdometry/CMakeLists.txt
```
add_executable(WheelOdometry wheel_odometry.cpp)
target_link_libraries(WheelOdometry ${catkin_LIBRARIES} ${Boost_LIBRARIES})
add_dependencies(WheelOdometry autorally_msgs_gencpp)

install(TARGETS
    WheelOdometry
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```
- wheel_odometry.launch
autorally/autorally_core/launch/wheel_odometry.launch

```
<launch>
  <node name="WheelOdometry" pkg="autorally_core" type="WheelOdometry" output="screen"/>
    <param name="vehicle_wheelbase" value="0.57785" />
    <param name="vehicle_width" value="0.3175" />
    <param name="using_sim" value="false" />

    <!-- note: the debug parameter delays the output of the angular velocity -->
    <param name="debug" value="false" />

    <!-- time_delay applies to the angular velocity calculation that lines data up with state estimator - only debug mode -->
    <param name="time_delay" value="0.2714" />

</launch>
```
- wheel_odometry.cpp
autorally/autorally_core/src/WheelOdometry/wheel_odometry.cpp

```
wheel_odometry.cpp
```
- wheel_odometry.h
autorally/autorally_core/src/WheelOdometry/wheel_odometry.h

```
wheel_odometry.h
```
- Another CMakeLists
autorally/autorally_core/CMakeLists.txt
```
https://github.com/AutoRally/autorally/blob/c62a7bb0efba9d583e86afb06a4749bd3feafad7/autorally_core/CMakeLists.txt
```
