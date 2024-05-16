cmake_minimum_required(VERSION 3.27)
set(CMAKE_CXX_STANDARD 20)
project(CircularBuffer)

include_directories(${PROJECT_SOURCE_DIR}/include)
file(GLOB all_SRCS
        "${PROJECT_SOURCE_DIR}/include/*.h"
        "${PROJECT_SOURCE_DIR}/source/*.cpp"
)
add_executable(CircularBuffer ${all_SRCS})

option(MATCH_TESTS "build tests (or no)" ON)
if (MATCH_TESTS)
    add_library(CircularBuffer_Lib SHARED include/CircularBuffer.h)
    set_target_properties(CircularBuffer_Lib PROPERTIES LINKER_LANGUAGE CXX)
    add_subdirectory(test)
endif ()