##############################################################################
# CMake
##############################################################################

cmake_minimum_required(VERSION 2.8.3)
project(zeroconf_avahi_demos)

set(CMAKE_VERBOSE_MAKEFILE TRUE)

##############################################################################
# Catkin
##############################################################################

find_package(catkin REQUIRED COMPONENTS zeroconf_avahi zeroconf_msgs)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${zeroconf_avahi_DIR})
find_package(Avahi REQUIRED)


set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")


catkin_package()
include_directories(include ${catkin_INCLUDE_DIRS} ${AVAHI_INCLUDE_DIR})

##############################################################################
# Project
##############################################################################

add_subdirectory(src)
add_subdirectory(scripts)

##############################################################################
# Installs
##############################################################################

install(DIRECTORY launch
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
install(DIRECTORY param
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

