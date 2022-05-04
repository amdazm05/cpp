cmake_minimum_required(VERSION 3.0)
set (SOURCE src/main.cpp)
# test is a reserved name for a lib so avoid using it
project(main)

set(C_STANDARD 99)
set(CMAKE_CXX_STANDARD 11)
# This sets is for creating a symbol table for 
# GDB and will be used for debugging

if (DEBUG_MODE)
    set(CMAKE_BUILD_TYPE DEBUG)
endif()

add_library(LIBRARIES 
    STATIC 
        ${PROJECT_SOURCE_DIR}/src/add/add.cpp
)

target_include_directories(LIBRARIES 
    PUBLIC
        ${PROJECT_SOURCE_DIR}/lib/add
)

add_executable(main ${SOURCE})
target_link_libraries(main PUBLIC LIBRARIES)
# If tests are to be compiled