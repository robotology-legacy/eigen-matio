# # Authors: Giulio Romualdi

cmake_minimum_required(VERSION 3.1)
project(EigenMatio VERSION 1.0 LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 14)

#list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

# Define the library target
add_library(EigenMatio INTERFACE)
target_include_directories(EigenMatio INTERFACE
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

include(CMakePackageConfigHelpers)
write_basic_package_version_file(
    "${PROJECT_BINARY_DIR}/EigenMatioConfigVersion.cmake"
    VERSION 0.1
    COMPATIBILITY AnyNewerVersion
)

install(TARGETS EigenMatio
    EXPORT EigenMatioTargets
    LIBRARY DESTINATION lib COMPONENT Runtime
    ARCHIVE DESTINATION lib COMPONENT Development
    RUNTIME DESTINATION bin COMPONENT Runtime
    PUBLIC_HEADER DESTINATION include COMPONENT Development
    BUNDLE DESTINATION bin COMPONENT Runtime
)

include(CMakePackageConfigHelpers)
configure_package_config_file(
    "${PROJECT_SOURCE_DIR}/cmake/EigenMatioConfig.cmake.in"
    "${PROJECT_BINARY_DIR}/EigenMatioConfig.cmake"
    INSTALL_DESTINATION lib/cmake/EigenMatio
)

install(EXPORT EigenMatioTargets DESTINATION lib/cmake/EigenMatio)
install(FILES "${PROJECT_BINARY_DIR}/EigenMatioConfigVersion.cmake"
              "${PROJECT_BINARY_DIR}/EigenMatioConfig.cmake"
        DESTINATION lib/cmake/EigenMatio)
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/ DESTINATION include)
