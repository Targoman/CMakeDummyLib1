cmake_minimum_required(VERSION 3.16)
project(CMakeBuildSampleLib VERSION 0.0.1)

include(./Targoman.cmake)
setup_bs_paths()

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS Core Test REQUIRED)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

add_subdirectory(3rdParty)

add_library(DummyLib1
    SHARED
    libsrc/libDummyLib1/clsSample.cpp
)
set_target_properties(DummyLib1
    PROPERTIES
    PUBLIC_HEADER
    libsrc/libDummyLib1/clsSample.h
)
target_link_libraries(DummyLib1 Qt5::Core)

export_public_headers(DummyLib1)