cmake_minimum_required(VERSION 2.8.3)
project(boteye_driver_ros)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/cmake/Modules/") 
message(STATUS "CMAKE_MODULE_PATH: ${CMAKE_MODULE_PATH}")
set (CMAKE_CXX_FLAGS "-std=c++11 -Wno-deprecated-declarations ${CMAKE_CXX_FLAGS}")
add_definitions(-D__DRIVER_NONE_RELEASE__)

find_package(Glog REQUIRED)
find_package(GFlags REQUIRED)
find_package(catkin REQUIRED COMPONENTS 
		image_transport 
		cv_bridge
		roscpp 
		std_msgs 
		sensor_msgs 
		)
find_package(OpenCV REQUIRED)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES boteye_driver_ros
  CATKIN_DEPENDS roscpp std_msgs 
  DEPENDS system_lib
)

include_directories(
  include 
  ${catkin_INCLUDE_DIRS}  
  ${CMAKE_CURRENT_SOURCE_DIR}/include/
)  

add_executable( driver_bringup 
	        src/driver_demo.cpp 
	        src/v4l2.cc 
		src/XP_sensor.cc 
		src/XP_sensor_driver.cc  
		src/helper/timer.cc
		src/helper/counter_32_to_64.cc
		src/helper/basic_image_utils.cc
		)  

target_link_libraries(driver_bringup ${OpenCV_LIBS} ${catkin_LIBRARIES}  glog gflags)  
