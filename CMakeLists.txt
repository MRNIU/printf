
# This file is a part of MRNIU/printf_bare_metal
# (https://github.com/MRNIU/printf_bare_metal).
#
# CMakeLists.txt for MRNIU/printf_bare_metal.

# 设置最小 cmake 版本
cmake_minimum_required(VERSION 3.27 FATAL_ERROR)

# 设置项目名与版本
project(
        printf_bare_metal
        VERSION 1.8.3
)

# 禁止原地编译
if (${PROJECT_SOURCE_DIR} STREQUAL ${PROJECT_BINARY_DIR})
    message(
            FATAL_ERROR
            "In-source builds not allowed. Please make a new directory (called a build directory) and run CMake from there."
    )
endif ()

add_subdirectory(src)

if (CMAKE_SYSTEM_PROCESSOR STREQUAL CMAKE_HOST_SYSTEM_PROCESSOR)
    # https://github.com/google/googletest.git
    add_subdirectory(3rd/googletest)
    include(GoogleTest)

    add_subdirectory(test)
endif ()
