cmake_minimum_required(VERSION 2.8.12)
project(qpOASES_catkin CXX)
set(qpOASES_VERSION "3.2.0")

include(ExternalProject)

ExternalProject_Add(
  qpOASES
  #SVN_REPOSITORY https://projects.coin-or.org/svn/qpOASES/stable/3.2
  #SVN_TRUST_CERT 1
  GIT_REPOSITORY https://github.com/humanoid-path-planner/qpoases.git
  GIT_TAG master
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CATKIN_DEVEL_PREFIX}
)

find_package(catkin REQUIRED)

file(MAKE_DIRECTORY ${CATKIN_DEVEL_PREFIX}/include)
catkin_package(
  INCLUDE_DIRS ${CATKIN_DEVEL_PREFIX}/include
  LIBRARIES qpOASES
)

install(
  DIRECTORY ${CATKIN_DEVEL_PREFIX}/include
  DESTINATION ${CMAKE_INSTALL_PREFIX}
  PATTERN ".svn" EXCLUDE
)
install(
  FILES ${CATKIN_DEVEL_PREFIX}/lib/pkgconfig/qpOASES.pc
  DESTINATION ${CMAKE_INSTALL_PREFIX}/lib/pkgconfig
)
install(
  FILES ${CATKIN_DEVEL_PREFIX}/lib/${CMAKE_SHARED_LIBRARY_PREFIX}qpOASES${CMAKE_SHARED_LIBRARY_SUFFIX}
  DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)
