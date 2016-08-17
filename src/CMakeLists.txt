# Specify the minimum version for CMake
cmake_minimum_required(VERSION 2.8)

# Project's name
project(hw)

find_package(OpenGL REQUIRED)

# Set the output folder where your program will be created
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR})

# The following folder will be included
include_directories("${PROJECT_SOURCE_DIR}")

# Add GLFW_LIBRARIES
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory("vendor/glfw")
# include_directories("vendor/glfw/include")

add_executable(hw ${PROJECT_SOURCE_DIR}/hw.cc)
# target_include_directories(hw ${OPENGL_INCLUDE_DIR})
target_link_libraries(hw glfw ${GLFW_LIBRARIES} ${OPENGL_glu_LIBRARY})
