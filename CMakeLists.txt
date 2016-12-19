cmake_minimum_required(VERSION 3.5)
project(imgui)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -O3 -pthread")
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "/usr/local/cmake_modules/")

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(GLEW REQUIRED)

set(SOURCE_FILES
    imgui_draw.cpp imgui.cpp)

add_library(imgui STATIC ${SOURCE_FILES})

target_link_libraries(imgui ${OPENGL_LIBRARIES})
target_link_libraries(imgui ${GLEW_LIBRARIES})
target_link_libraries(imgui glfw)
target_link_libraries(imgui ${Boost_LIBRARIES})

target_include_directories(imgui PUBLIC ${OPENGL_INCLUDE_DIR})
target_include_directories(imgui PUBLIC ${GLEW_INCLUDE_DIR})
target_include_directories(imgui PUBLIC ${Boost_INCLUDE_DIRS})

