cmake_minimum_required(VERSION 3.1)
project(PackageTest CXX)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(wasmtime-cpp REQUIRED)

add_executable(example example.cpp)
target_link_libraries(example PRIVATE wasmtime-cpp::wasmtime-cpp)
target_compile_definitions(example PUBLIC WASMTIME_EXAMPLES_PATH="${CMAKE_SOURCE_DIR}")
set_target_properties(example PROPERTIES
    CXX_EXTENSIONS OFF
    CXX_STANDARD 17
)
