# The Flutter tooling requires that developers have CMake 3.10 or later
# installed. You should not increase this version, as doing so will cause
# the plugin to fail to compile for some customers of the plugin.
cmake_minimum_required(VERSION 3.10)

project(libusb_library VERSION 0.0.1 LANGUAGES C)

set(PLATFORM_SRC
  "libusb/os/events_windows.c"
  "libusb/os/threads_windows.c"
)

set(OS_SRC
  "libusb/libusb-1.0.def"
  "libusb/libusb-1.0.rc"
  "libusb/os/windows_common.c"
  "libusb/os/windows_usbdk.c"
  "libusb/os/windows_winusb.c"
)

set(LIBUSB_SRC
  "libusb/core.c"
  "libusb/descriptor.c"
  "libusb/hotplug.c"
  "libusb/io.c"
  "libusb/strerror.c"
  "libusb/sync.c"
  ${PLATFORM_SRC}
  ${OS_SRC}
)


include_directories(
  "msvc"
  "libusb"
)

add_library(libusb SHARED
  ${LIBUSB_SRC}
)

set_target_properties(libusb PROPERTIES
  OUTPUT_NAME "libusb-1.0"
)

target_compile_definitions(libusb PUBLIC DART_SHARED_LIB)