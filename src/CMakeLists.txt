
# This file is a part of MRNIU/printf_bare_metal
# (https://github.com/MRNIU/printf_bare_metal).
#
# CMakeLists.txt for MRNIU/printf_bare_metal.

add_library(${PROJECT_NAME} STATIC
        printf_bare_metal.c
)

target_include_directories(${PROJECT_NAME} PUBLIC
        $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/src/include>
        $<INSTALL_INTERFACE:include>
)

target_compile_options(${PROJECT_NAME} PRIVATE
        $<$<CONFIG:Release>:-O3;-Werror>
        -Wall
        -Wextra
        -ffreestanding
)

target_link_options(${PROJECT_NAME} PRIVATE
        -no-pie
)

set_target_properties(${PROJECT_NAME} PROPERTIES PUBLIC_HEADER "include/printf_bare_metal.h")
