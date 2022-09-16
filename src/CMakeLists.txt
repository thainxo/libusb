# The Flutter tooling requires that developers have CMake 3.10 or later
# installed. You should not increase this version, as doing so will cause
# the plugin to fail to compile for some customers of the plugin.
cmake_minimum_required(VERSION 3.10)

project(libusb_library VERSION 0.0.1 LANGUAGES C)

add_library(libusb SHARED
  "libusb.c"
)

set_target_properties(libusb PROPERTIES
  PUBLIC_HEADER libusb.h
  OUTPUT_NAME "libusb"
)

target_compile_definitions(libusb PUBLIC DART_SHARED_LIB)