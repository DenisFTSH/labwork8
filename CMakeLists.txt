cmake_minimum_required(VERSION 3.27)
project(labwork8_Denis224466)

set(CMAKE_CXX_STANDARD 23)

include_directories(bin)
include_directories(lib)
include_directories(tests)

add_executable(labwork8_Denis224466
        bin/main.cpp
        lib/BST.h)
include(FetchContent)

FetchContent_Declare(
        googletest
        GIT_REPOSITORY https://github.com/google/googletest.git
        GIT_TAG release-1.12.1
)

# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(
        testing
        tests/testing.cpp
)

target_link_libraries(
        testing
        GTest::gtest_main
)

target_include_directories(testing PUBLIC ${PROJECT_SOURCE_DIR})

include(GoogleTest)

gtest_discover_tests(testing)