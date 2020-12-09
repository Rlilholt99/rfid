cmake_minimum_required(VERSION 2.8.3)
project(idscanner)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS roscpp geometry_msgs move_base_msgs actionlib)

###################################
## catkin specific configuration ##
###################################
catkin_package(
)

###########
## Build ##
###########
include_directories(
  ${catkin_INCLUDE_DIRS}
)

# Declare Kill Turtles C++ executable and rename to short name (in case catkin_make is used).
add_executable(${PROJECT_NAME}idscanner src/rfid_startup.cpp)
set_target_properties(${PROJECT_NAME}idscanner PROPERTIES OUTPUT_NAME rfid_startup PREFIX "")
# Link to Catkin libraries
target_link_libraries(${PROJECT_NAME}idscanner
  ${catkin_LIBRARIES}
)

#############
## Install ##
#############

# Mark executables for installation
install(TARGETS
  ${PROJECT_NAME}idscanner
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)