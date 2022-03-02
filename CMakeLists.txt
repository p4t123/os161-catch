cmake_minimum_required(VERSION 3.20)
project(os161 C)

set(CMAKE_CXX_STANDARD 11)

#set(GCC_COMPILE_FLAGS -Wall -Werror -Wvla -O0 -nostdlib -fno-builtin)
set(GCC_COMPILE_FLAGS -nostdlib -fno-builtin)

SET(CMAKE_BUILD_TYPE Debug)

include_directories(kern/include)
include_directories(kern/compile/ASST0)
include_directories(kern/compile/ASST0/includelinks)
include_directories(kern/compile)

include_directories(userland/include)

file(GLOB_RECURSE INCLUDE_DIRECTORIES "${PROJECT_SOURCE_DIR}/*.h")
file(GLOB_RECURSE SOURCE_FILES "${PROJECT_SOURCE_DIR}/*.c")

add_executable (os161 ${INCLUDE_DIRECTORIES} ${SOURCE_FILES})

# Enabling tests
enable_testing()

add_subdirectory(test/unit)
