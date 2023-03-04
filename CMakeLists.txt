cmake_minimum_required(VERSION 2.8)
project(tinycthreadpool C)

add_library(tinycthreadpool threadpool.c tinycthread.c)
set_target_properties(tinycthreadpool PROPERTIES PUBLIC_HEADER "threadpool.h;tinycthread.h")

install(TARGETS tinycthreadpool)