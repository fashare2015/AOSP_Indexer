cmake_minimum_required(VERSION 3.5)
add_definitions(-DANDROID)

set(PROJECT_DIR "${CMAKE_HOME_DIRECTORY}")
#set(CMAKE_C_COMPILER ${PROJECT_DIR}/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.9/bin/arm-linux-androideabi-gcc)
#set(CMAKE_CXX_COMPILER ${PROJECT_DIR}/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.9/bin/arm-linux-androideabi-gcc)
project(android)

include_directories(kernel/include)
include_directories(prebuilts/ndk/9/platforms/android-19/arch-arm/usr/include)

include_directories(external/libcxx/include)
include_directories(external/libpcap)
include_directories(external/skia/include)
include_directories(external/skia/include/core)

include_directories(bionic/libc)
include_directories(bionic/libc/kernel/uapi)
include_directories(bionic/libc/include)
include_directories(bionic/libc/arch-arm/include)
include_directories(bionic/libstdc++/include)
include_directories(bionic/libc/upstream-netbsd/libc/include)
include_directories(bionic/libthread_db/include)
include_directories(bionic/libm/include)


include_directories(frameworks/native/include)
include_directories(frameworks/base/include/)
include_directories(frameworks/av/include/)
include_directories(libnativehelper/include/)
include_directories(libnativehelper/include/nativehelper)
include_directories(system/core/include)
include_directories(hardware/libhardware/include)
include_directories(hardware/rockchip/camera/SiliconImage/include)
include_directories(hardware/rockchip/camera/SiliconImage/include/isp_cam_api)
include_directories(hardware/rockchip/camera/SiliconImage/isi/include)

file(GLOB_RECURSE BIONIC_SOURCES "bionic/*.cpp" "bionic/*.c" "bionic/*.cxx" "bionic/*.h")
file(GLOB_RECURSE HARDWARE_SOURCES "hardware/*.cpp" "hardware/*.c" "hardware/*.cxx" "hardware/*.h")
file(GLOB_RECURSE FRAMEWORK_SOURCES "frameworks/*.cpp" "frameworks/*.c" "frameworks/*.cxx" "frameworks/*.h")
file(GLOB_RECURSE SYSTEM_SOURCES "system/*.cpp" "system/*.c" "system/*.cxx" "system/*.h")
file(GLOB_RECURSE LIBCORE_SOURCES "libcore/*.cpp" "libcore/*.c" "libcore/*.cxx" "libcore/*.cc" "libcore/*.h")


add_executable(android ${BIONIC_SOURCES} ${LIBCORE_SOURCES} ${HARDWARE_SOURCES} ${FRAMEWORK_SOURCES} ${SYSTEM_SOURCES} )
