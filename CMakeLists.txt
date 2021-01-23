cmake_minimum_required(VERSION 3.13)

project(cuda_test LANGUAGES CXX CUDA)

set(CMAKE_CUDA_STANDARD 14)
set(CMAKE_CXX_STANDARD 14)


include_directories(include)

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR})

FIND_PACKAGE(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIR})

add_executable(cuda_test src/main.cu)

find_package(CUDA)
target_link_libraries(cuda_test ${GLUT_LIBRARY} ${OPENGL_LIBRARY})

set_target_properties(
        cuda_test
        PROPERTIES
        CUDA_SEPARABLE_COMPILATION ON)