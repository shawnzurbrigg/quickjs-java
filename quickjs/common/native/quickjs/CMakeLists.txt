cmake_minimum_required(VERSION 3.4.1)
project(quickjs C)

set(CMAKE_C_STANDARD 99)

file(GLOB sources "*.c")
add_library(quickjs SHARED ${sources})
target_compile_definitions(quickjs PUBLIC CONFIG_VERSION="${QUICKJS_VERSION}")
target_include_directories(quickjs PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(quickjs)
