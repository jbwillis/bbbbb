cmake_minimum_required(VERSION 3.14 FATAL_ERROR)

# create project
project(bbbbb)

set(CMAKE_CXX_STANDARD 20)

# add dependencies
list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
include(FindCPM)

CPMAddPackage("gh:fmtlib/fmt#7.1.3")

# ###########################################################
# OPTIONS
option(BBBBB_BUILD_TESTS "Build the tests" ON)

# add subdirectories
add_subdirectory(src)
include_directories(src)

# ###########################################################
# TESTING
if(BBBBB_BUILD_TESTS)
    CPMAddPackage("gh:catchorg/Catch2@3.4.0")
endif()

# link dependencies
target_link_libraries(main fmt::fmt)