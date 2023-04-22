cmake_minimum_required(VERSION 3.14)

project(imguiInMac LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core)

set(GLFW_DIR, "/usr/local/lib")

include_directories("./imgui")

include_directories("/usr/local/include")
link_directories("/usr/local/lib")
link_directories("/System/Library/Frameworks")

add_definitions(-DGLFW_STATIC)

set(IMGUI_DIR ./imgui/)

file(GLOB ALL_SOURCE ${IMGUI_DIR}/*.cpp)

file(GLOB_RECURSE ALL_HEAD ${IMGUI_DIR}/*.h)

add_executable(imguiInMac
  ${ALL_SOURCE}
  ${ALL_HEAD}
  main.cpp
)

target_link_libraries(imguiInMac Qt${QT_VERSION_MAJOR}::Core
    libglfw3.a
    "-framework Cocoa"
    "-framework OpenGL"
    "-framework CoreVideo"
    "-framework IOKit")

install(TARGETS imguiInMac
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
