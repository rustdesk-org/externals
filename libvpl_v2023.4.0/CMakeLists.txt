cmake_minimum_required(VERSION 3.12)
project(vpl)

set(CMAKE_CXX_STANDARD 11)

set(SDK_DIR ${CMAKE_SOURCE_DIR})
set(LIBVPL_DIR ${SDK_DIR}/libvpl)
set(LEGACY_TOOL_DIR ${SDK_DIR}/tools/legacy)
set(SAMEPLE_COMMON_DIR ${LEGACY_TOOL_DIR}/sample_common)

# Source files
set(SOURCES
    ${LIBVPL_DIR}/src/mfx_dispatcher_vpl.cpp
    ${LIBVPL_DIR}/src/mfx_dispatcher_vpl_config.cpp
    ${LIBVPL_DIR}/src/mfx_dispatcher_vpl_loader.cpp
    ${LIBVPL_DIR}/src/mfx_dispatcher_vpl_log.cpp
    ${LIBVPL_DIR}/src/mfx_dispatcher_vpl_lowlatency.cpp
    ${LIBVPL_DIR}/src/mfx_dispatcher_vpl_msdk.cpp
    ${LIBVPL_DIR}/src/windows/mfx_dispatcher_main.cpp
    ${LIBVPL_DIR}/src/windows/mfx_critical_section.cpp
    ${LIBVPL_DIR}/src/windows/mfx_dispatcher.cpp
    ${LIBVPL_DIR}/src/windows/mfx_dispatcher_log.cpp
    ${LIBVPL_DIR}/src/windows/mfx_driver_store_loader.cpp
    ${LIBVPL_DIR}/src/windows/mfx_dxva2_device.cpp
    ${LIBVPL_DIR}/src/windows/mfx_function_table.cpp
    ${LIBVPL_DIR}/src/windows/mfx_library_iterator.cpp
    ${LIBVPL_DIR}/src/windows/mfx_load_dll.cpp
    ${LIBVPL_DIR}/src/windows/mfx_win_reg_key.cpp
    ${LIBVPL_DIR}/src/mfx_config_interface/mfx_config_interface.cpp
    ${LIBVPL_DIR}/src/mfx_config_interface/mfx_config_interface_string_api.cpp
    ${SAMEPLE_COMMON_DIR}/src/sample_utils.cpp
    ${SAMEPLE_COMMON_DIR}/src/base_allocator.cpp
    ${SAMEPLE_COMMON_DIR}/src/d3d11_allocator.cpp
    ${SAMEPLE_COMMON_DIR}/src/avc_bitstream.cpp
    ${SAMEPLE_COMMON_DIR}/src/avc_spl.cpp
    ${SAMEPLE_COMMON_DIR}/src/avc_nal_spl.cpp
    ${SAMEPLE_COMMON_DIR}/src/vm/time.cpp
    ${SAMEPLE_COMMON_DIR}/src/vm/atomic.cpp
    ${SAMEPLE_COMMON_DIR}/src/vm/shared_object.cpp
    ${SAMEPLE_COMMON_DIR}/src/vm/thread_windows.cpp
)

# Include directories
set(VPL_INCLUDE_DIRS
    ${LIBVPL_DIR}
    ${SDK_DIR}/api
    ${SAMEPLE_COMMON_DIR}/include
    ${SAMEPLE_COMMON_DIR}/include/vm
    ${LEGACY_TOOL_DIR}/media_sdk_compatibility_headers
)
include_directories(${VPL_INCLUDE_DIRS})

# Build target
add_library(vpl STATIC ${SOURCES})

# Compiler definitions
target_compile_definitions(vpl PRIVATE
    NOMINMAX
    MFX_DEPRECATED_OFF
    MFX_D3D11_SUPPORT
)