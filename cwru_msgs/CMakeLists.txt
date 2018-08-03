cmake_minimum_required(VERSION 2.8.3)
project(cwru_msgs)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  actionlib
  actionlib_msgs
  geometry_msgs
  message_generation
  nav_msgs
  std_msgs
  trajectory_msgs
)

find_package(Boost REQUIRED COMPONENTS system)

 add_message_files(
   FILES
   cRIOSensors.msg
   NavSatStatus.msg
   NavSatFix.msg
   Pose.msg
   PowerState.msg
   Sonar.msg
   DesiredState.msg
   ErrorCode.msg
   Path.msg
   PathSegment.msg
   VecOfDoubles.msg
   VecOfStrings.msg
   PatchParams.msg
   PoseAffine.msg
   PoseAffineStamped.msg
   VecOfPoseAffines.msg
   VecOfPoseAffinesStamped.msg
 )

generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs

)
catkin_package(
  CATKIN_DEPENDS actionlib actionlib_msgs geometry_msgs nav_msgs std_msgs trajectory_msgs
  DEPENDS message_runtime
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_dependencies(${p} ${catkin_EXPORTED_TARGETS} ${PROJECT_NAME}_generate_messages_cpp)
