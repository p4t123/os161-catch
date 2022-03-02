project(os161-test)

# These are compiler flags specific for running tests.
#set(GCC_COMPILE_FLAGS_TEST -Wno-unused-function -Wno-unused-variable -nostdlib )
set(GCC_COMPILE_FLAGS_TEST -fno-builtin)

# Download Google Test
include(FetchContent)
FetchContent_Declare(
        Catch2
        GIT_REPOSITORY https://github.com/catchorg/Catch2.git
        GIT_TAG        v2.13.1)

FetchContent_MakeAvailable(Catch2)

## Create tests exe here
add_executable(test_main kern/main/test_main.cpp)

target_link_libraries(test_main Catch2::Catch2)
target_compile_options(test_main PRIVATE ${GCC_COMPILE_FLAGS} ${GCC_COMPILE_FLAGS_TEST})
add_test(test_main test_main)

