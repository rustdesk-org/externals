cmake_minimum_required(VERSION 3.12)
project(amf)

set(CMAKE_CXX_STANDARD 11)

set(AMF_DIR ${CMAKE_SOURCE_DIR})
set(AMF_COMMON_DIR ${AMF_DIR}/amf/public/common)

# Source files
set(SOURCES
    ${AMF_COMMON_DIR}/AMFFactory.cpp
    ${AMF_COMMON_DIR}/AMFSTL.cpp
    ${AMF_COMMON_DIR}/Thread.cpp
    ${AMF_COMMON_DIR}/TraceAdapter.cpp
    ${AMF_COMMON_DIR}/Windows/ThreadWindows.cpp
)

# Include directories
set(AMF_INCLUDE_DIRS
    ${AMF_DIR}/amf
    ${AMF_COMMON_DIR}
)
include_directories(${AMF_INCLUDE_DIRS})

# Build target
add_library(amf STATIC ${SOURCES})
