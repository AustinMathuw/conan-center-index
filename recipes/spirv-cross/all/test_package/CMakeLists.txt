cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES C)

# FIXME: this is not the official way to find spirv-cross components
find_package(spirv-cross REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.c)
if(TARGET spirv-cross-c)
    target_link_libraries(${PROJECT_NAME} PRIVATE spirv-cross-c)
elseif(TARGET spirv-cross-c-shared)
    target_link_libraries(${PROJECT_NAME} PRIVATE spirv-cross-c-shared)
endif()
