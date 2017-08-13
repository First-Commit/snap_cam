cmake_minimum_required(VERSION 2.8)

project(cameraTest)

include_directories(
  src
  inc
  /home/linaro/libjpeg-turbo
)

add_executable(cam_test test/camera_test.cpp)

LINK_DIRECTORIES(
  /usr/lib
  /home/linaro/libjpeg-turbo/build/.libs
  )

ADD_LIBRARY(turbojpeg SHARED IMPORTED)
set_property(TARGET turbojpeg PROPERTY IMPORTED_LOCATION "/home/linaro/libjpeg-turbo/build/.libs/libturbojpeg.so")

TARGET_LINK_LIBRARIES(cam_test camera turbojpeg)
