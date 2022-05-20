cmake_minimum_required(VERSION 3.10)

project(formatter_ex)

add_library(lib2 STATIC formatter_ex.cpp)


target_include_directories(lib2 PUBLIC 
                            ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib)

target_link_libraries(lib2 lib1)
