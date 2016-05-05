cmake_minimum_required(VERSION 2.8.3)
project(skeleton_tracker)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  geometry_msgs
  image_transport
  kdl_conversions
  openni2_camera
  pcl_conversions
  pcl_ros
  roscpp
  roslib
  tf
  message_generation
  actionlib
  actionlib_msgs
)

#find_package(opencv REQUIRED)

include_directories(
    include
    ${catkin_INCLUDE_DIRS}
)

add_message_files(
   FILES
   user_IDs.msg
   joint_message.msg
   skeleton_message.msg
   skeleton_complete.msg
   skeleton_tracker_state.msg
)

## Generate services in the 'srv' folder
add_service_files(
   FILES
   DeleteImages.srv
 )


add_action_files(
  DIRECTORY action
  FILES skeleton.action
)

generate_messages(
    DEPENDENCIES geometry_msgs actionlib_msgs
)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES skeleton_tracker
  CATKIN_DEPENDS cv_bridge geometry_msgs image_transport kdl_conversions openni2_camera pcl_conversions pcl_ros roscpp roslib tf actionlib_msgs
  DEPENDS system_lib opencv message_runtime
)


