cmake_minimum_required(VERSION 3.5)
project(deepstream_test-app)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread -g")
find_package(OpenCV REQUIRED)
# directory of opencv headers
include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIBRARY_DIRS})
include_directories(
	/opt/nvidia/deepstream/deepstream-5.1/sources/includes
	/usr/include/gstreamer-1.0
	/usr/include/glib-2.0
	/usr/lib/x86_64-linux-gnu/glib-2.0/include
        /usr/local/cuda-11.1/include
	)
link_directories(
    /usr/local/cuda-11.1/lib64
    /opt/nvidia/deepstream/deepstream-5.1/lib
)
link_libraries(
    gstreamer-1.0
    gobject-2.0
    glib-2.0
    cudart
    nvdsgst_meta
    nvds_meta
    cuda
    ${OpenCV_LIBS}
	)

add_executable(deepstream_test1_app deepstream_test1_app.cpp)
