cmake_minimum_required(VERSION 2.8.3)
project(kuri_mbzirc_challenge_3)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS roscpp cv_bridge rospy   sensor_msgs image_transport )


###################################
## catkin specific configuration ##
###################################
catkin_package(
    CATKIN_DEPENDS
)

include_directories(include ${catkin_INCLUDE_DIRS}
			    ${OpenCV_INCLUDE_DIRS})

#############
## Install ##
#############
install(DIRECTORY launch urdf config
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  USE_SOURCE_PERMISSIONS)
########################
# color detection node #
########################

add_executable(color_detection src/CD.cpp)
target_link_libraries(color_detection ${catkin_LIBRARIES}  ${OpenCV_LIBRARIES})
add_dependencies(color_detection ${PROJECT_NAME}_gencfg ${PROJECT_NAME}_generate_messages_cpp)

#############
## Testing ##
#############
if(CATKIN_ENABLE_TESTING)
  find_package(catkin REQUIRED COMPONENTS rostest roslaunch)
#  roslaunch_add_file_check(launch/task.launch)
endif()
