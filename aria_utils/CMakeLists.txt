cmake_minimum_required(VERSION 2.8.3)
project(aria_utils)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  sensor_msgs
)

################################################
## Declare ROS messages, services and actions ##
################################################


###################################
## catkin specific configuration ##
###################################
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES utils
#  CATKIN_DEPENDS other_catkin_pkg
#  DEPENDS system_lib
)

###########
## Build ##
###########

find_package(jsk_gui_msgs REQUIRED)

include_directories(${jsk_gui_msgs_INCLUDE_DIRS})

include_directories(
  ${catkin_INCLUDE_DIRS}
  ../aria_2ndparty/src/common
  ../aria_2ndparty/src/sensors
  ../aria_2ndparty/src/actuators
  ../aria_2ndparty/src/utils
  ## includes/jsk_gui_msgs
)

add_executable(ps3_to_web src/ps3_to_web.cc ../aria_2ndparty/src/common/ssb_common_of.cc ../aria_2ndparty/src/common/ssb_common_vec.cc ../aria_2ndparty/src/utils/ssb_utils_model.cc)

add_executable(virtual_mcu_core src/virtual_mcu_core.cc ../aria_2ndparty/src/common/ssb_common_of.cc ../aria_2ndparty/src/common/ssb_common_vec.cc ../aria_2ndparty/src/utils/ssb_utils_model.cc ../aria_2ndparty/src/utils/ssb_utils_interpolation.cc)

add_executable(voice_to_pose src/voice_to_pose.cc ../aria_2ndparty/src/common/ssb_common_of.cc ../aria_2ndparty/src/common/ssb_common_vec.cc)

target_link_libraries(ps3_to_web
  ${catkin_LIBRARIES}
)

target_link_libraries(virtual_mcu_core
  ${catkin_LIBRARIES}
)

target_link_libraries(voice_to_pose
  ${catkin_LIBRARIES}
)

#############
## Install ##
#############


#############
## Testing ##
#############

