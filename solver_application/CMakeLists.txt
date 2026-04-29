cmake_minimum_required(VERSION 3.10...3.20)
project(solver)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(solver equation.cpp)

target_link_libraries(solver PRIVATE
    formatter_ex
    solver_lib
)







