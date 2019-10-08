cmake_minimum_required(VERSION 3.5)
project(glpoints-sandbox)

set(CMAKE_CXX_STANDARD 11)

find_package(glfw3 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
find_package(Threads REQUIRED)


add_library(imgui STATIC
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui_demo.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui_draw.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui_widgets.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/examples/imgui_impl_glfw.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/examples/imgui_impl_opengl3.cpp
)

target_include_directories(imgui
    PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/examples
)

add_executable(glpoints-sandbox main.cpp)

target_include_directories(glpoints-sandbox
    PRIVATE
    ${GLFW3_INCLUDE_DIR}
    ${OPENGL_INCLUDE_PATH}
    ${GLEW_INCLUDE_DIRS}
)

target_link_libraries(glpoints-sandbox
    PRIVATE
    ${GLFW3_LIBRARY}
    ${OPENGL_LIBRARIES}
    ${GLEW_LIBRARIES}
    imgui
)
