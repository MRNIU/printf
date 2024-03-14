
# This file is a part of MRNIU/printf
# (https://github.com/MRNIU/printf).
#
# CMakeLists.txt for MRNIU/printf.

add_library(${PROJECT_NAME} STATIC
        printf.c
)

target_include_directories(${PROJECT_NAME} PUBLIC
        $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/src/include>
        $<INSTALL_INTERFACE:include>
)

target_compile_options(${PROJECT_NAME} PRIVATE
        $<$<CONFIG:Release>:-O3;-Werror>
        -Wall
        -Wextra
)

set_target_properties(${PROJECT_NAME} PROPERTIES PUBLIC_HEADER "include/printf.h")
