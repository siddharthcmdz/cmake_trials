cmake_minimum_required(VERSION 3.17)
project(BasicsOfCMake)

add_executable(BasicsOfCMake ./main.h ./main.cpp)

target_include_directories(BasicsOfCMake PUBLIC ./)
