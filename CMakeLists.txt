cmake_minimum_required(VERSION 2.8.3)
project(dji_px4)

## Find catkin and any catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs mavros_msgs uav_abstraction_layer message_generation)

## Generate services in the 'srv' folder
add_service_files(
  FILES
  DroneTaskControl.srv
  SDKControlAuthority.srv
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  std_msgs
)

## Declare a catkin package
catkin_package()

## Build talker and listener
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(dji_px4_interface scripts/dji_px4_interface.cpp)
target_link_libraries(dji_px4_interface ${catkin_LIBRARIES})

add_executable(dji_client scripts/dji_client.cpp)
target_link_libraries(dji_client ${catkin_LIBRARIES})