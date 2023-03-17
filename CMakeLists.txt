cmake_minimum_required(VERSION 2.8)
project(tinycthreadpool C)

if(BUILD_SHARED_LIBS AND MSVC)
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
endif()

add_library(tinycthreadpool threadpool.c tinycthread.c)
set_target_properties(tinycthreadpool PROPERTIES PUBLIC_HEADER "threadpool.h;tinycthread.h")

install(TARGETS tinycthreadpool)