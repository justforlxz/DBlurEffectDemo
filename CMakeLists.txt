cmake_minimum_required(VERSION 3.7)

set(VERSION 4.0)

#set(CMAKE_VERBOSE_MAKEFILE ON)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_FLAGS "-g -Wall")
set(BIN_NAME "dblureffectdemo")

set(SRCS
src/main.cpp
src/widget.h
src/widget.cpp
)

find_package(PkgConfig REQUIRED)
find_package(DtkWidget REQUIRED)
find_package(Qt5 COMPONENTS Core Gui Widgets REQUIRED)

add_executable(${BIN_NAME} ${SRCS})
target_include_directories(${BIN_NAME} PUBLIC
                                        ${DtkWidget_INCLUDE_DIRS}
                                        ${Qt5Gui_PRIVATE_INCLUDE_DIRS}
                                        ${PROJECT_BINARY_DIR}
)

target_link_libraries(${BIN_NAME} PRIVATE
        ${DtkWidget_LIBRARIES}
        Qt5::Core
        Qt5::Gui
        Qt5::Widgets
        ${PROCPS_LIBRARIES}
)
