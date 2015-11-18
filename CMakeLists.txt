cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project (reflexxes_type2)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)

catkin_package()

include_directories(include)

add_custom_target(
  reflexxes
  COMMAND make all64
  WORKING_DIRECTORY Linux
)

message(${CATKIN_PACKAGE_INCLUDE_DESTINATION})
message(${CMAKE_CURRENT_SOURCE_DIR})

## Mark cpp header files for installation
install(DIRECTORY include/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
)

## Mark other files for installation (e.g. launch and bag files, etc.)
install(
  FILES ${CMAKE_CURRENT_SOURCE_DIR}/Linux/x64/release/lib/shared/libReflexxesTypeII.so
  DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)
