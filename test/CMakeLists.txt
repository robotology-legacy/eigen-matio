# Authors: Giulio Romualdi
# CopyPolicy: Released under the terms of the LGPLv2.1 or later

cmake_minimum_required(VERSION 3.1)

set (CMAKE_CXX_STANDARD 11)

project(EigenMatio-Example)

find_package(EigenMatio CONFIG REQUIRED)
include_directories(SYSTEM ${EIGEN3_INCLUDE_DIR})

add_executable(mation_read_test read_test.cpp)
target_link_libraries(mation_read_test EigenMatio "-lmatio")
