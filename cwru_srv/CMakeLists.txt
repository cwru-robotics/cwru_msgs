cmake_minimum_required(VERSION 2.8.3)
project(cwru_srv)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  geometry_msgs
  nav_msgs
  roscpp
  std_msgs
  genmsg
)

add_service_files(DIRECTORY srv  
FILES simple_bool_service_message.srv
  simple_int_service_message.srv
  simple_float_service_message.srv
  arm_nav_service_message.srv
  IM_node_service_message.srv
  path_service_message.srv
  )

generate_messages(
  DEPENDENCIES
  std_msgs  
  geometry_msgs
  nav_msgs
)

catkin_package(
  CATKIN_DEPENDS message_runtime geometry_msgs nav_msgs roscpp std_msgs
)

include_directories(
 include ${catkin_INCLUDE_DIRS}
)

add_executable(cwru_srv_trivial_node src/example_ros_service.cpp)

add_dependencies(cwru_srv_trivial_node cwru_srv_generate_messages_cpp)

target_link_libraries(cwru_srv_trivial_node
  ${catkin_LIBRARIES} )
