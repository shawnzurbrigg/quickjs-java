cmake_minimum_required(VERSION 3.4.1)
project(quickjs-jni CXX)

add_subdirectory(quickjs)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_COMPILER "clang++")
add_compile_options(-stdlib=libc++)

find_package(JNI)
include_directories(${JNI_INCLUDE_DIRS})

file(GLOB sources "*.cpp")
add_library(quickjs-jni SHARED ${sources})
target_compile_definitions(quickjs-jni PUBLIC CONFIG_VERSION="${QUICKJS_VERSION}")
target_link_libraries(quickjs-jni PRIVATE quickjs)
