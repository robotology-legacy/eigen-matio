# Authors: Giulio Romualdi, Stefano Dafarra
# CopyPolicy: Released under the terms of the LGPLv2.1 or later

configure_file("${CMAKE_CURRENT_SOURCE_DIR}/FolderPath.h.in" "${CMAKE_CURRENT_BINARY_DIR}/FolderPath.h" @ONLY)

add_executable(mation_read_test read_test.cpp)
target_link_libraries(mation_read_test EigenMatio::EigenMatio)
target_include_directories(mation_read_test PUBLIC ${CMAKE_CURRENT_BINARY_DIR})

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/test.mat ${CMAKE_BINARY_DIR}/test.mat COPYONLY)

add_test(NAME mation_read_test COMMAND mation_read_test)
