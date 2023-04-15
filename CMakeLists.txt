cmake_minimum_required(VERSION 3.15)
project(tinycthreadpool C)

if(BUILD_SHARED_LIBS AND MSVC)
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
endif()

find_package(tinycthread REQUIRED)

add_library(tinycthreadpool threadpool.c)
target_link_libraries(${PROJECT_NAME} tinycthread::tinycthread)

set_target_properties(tinycthreadpool PROPERTIES PUBLIC_HEADER "threadpool.h")

install(TARGETS tinycthreadpool)
