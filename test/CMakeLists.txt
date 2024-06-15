
# This file is a part of MRNIU/printf_bare_metal
# (https://github.com/MRNIU/printf_bare_metal).
#
# CMakeLists.txt for MRNIU/printf_bare_metal.

# 设置项目名与版本
project(
        printf_bare_metal_test
)

enable_language(CXX)

enable_testing()

add_executable(${PROJECT_NAME}
        test_suite.cpp
)

target_compile_options(${PROJECT_NAME} PRIVATE
        -Wall
        -Wextra
)

# 添加要链接的库
target_link_libraries(${PROJECT_NAME} PRIVATE
        printf_bare_metal
        gtest_main
)

add_dependencies(${PROJECT_NAME}
        printf_bare_metal
)

gtest_discover_tests(${PROJECT_NAME})
