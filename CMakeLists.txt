cmake_minimum_required(VERSION 3.10)
project(SimpleGameEngine)

set(CMAKE_CXX_STANDARD 17)

# Add source files
set(SOURCES src/main.cpp)

# Include directories
include_directories(include)

# Manually specify GLFW paths if necessary
set(GLFW3_INCLUDE_DIRS "/usr/include/GLFW")
set(GLFW3_LIBRARIES "/usr/lib/x86_64-linux-gnu/libglfw.so")
include_directories(${GLFW3_INCLUDE_DIRS})
link_libraries(${GLFW3_LIBRARIES})

# Find and link GLEW
set(GLEW_INCLUDE_DIRS "/usr/include/GL")
set(GLEW_LIBRARIES "/usr/lib/x86_64-linux-gnu/libGLEW.so")
include_directories(${GLEW_INCLUDE_DIRS})
link_libraries(${GLEW_LIBRARIES})

# Find and link OpenGL
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR})
link_libraries(${OPENGL_LIBRARIES})

# Set OpenGL preference to GLVND
# set(OpenGL_GL_PREFERENCE "GLVND")

# Suppress CMP0072 warning
# cmake_policy(SET CMP0072 OLD)

# Add executable
add_executable(SimpleGameEngine ${SOURCES})