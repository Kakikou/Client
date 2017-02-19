cmake_minimum_required(VERSION 3.3)
project(BaseClient)

################################
# GTest
################################
add_subdirectory(googletest)
enable_testing()
include_directories(${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})
###############################

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES
        main.cpp
        src/Socket.cpp
        src/NetworkBuffer.cpp)

set(INCLUDES
        src/Socket.h
        src/IBuffer.h
        src/NetworkBuffer.h
        src/Protocol.h)

add_executable(BaseClient ${SOURCE_FILES} ${INCLUDES})

################################
# Unit Tests
################################
# Add test cpp file
add_executable( runUnitTests test/test.cpp )
# Link test executable against gtest & gtest_main
target_link_libraries(runUnitTests gtest gtest_main)
add_test( runUnitTests runUnitTests )