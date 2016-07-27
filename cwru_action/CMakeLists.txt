cmake_minimum_required(VERSION 2.8.3)
project(cwru_action)

find_package(catkin REQUIRED COMPONENTS
  actionlib
  actionlib_msgs
  message_generation
  geometry_msgs
  std_msgs
  trajectory_msgs
)

# Generate actions in the 'action' folder
add_action_files(
  FILES
  cart_move.action
  cwru_baxter_cart_move.action
  merry_get_can.action
  traj.action
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs
  trajectory_msgs
  actionlib_msgs
)

catkin_package(
  CATKIN_DEPENDS actionlib actionlib_msgs std_msgs trajectory_msgs
  DEPENDS message_runtime
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)
