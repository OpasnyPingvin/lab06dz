cmake_minimum_required(VERSION 3.10...3.20)
project(FormatterInc)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(formatter_lib)
add_subdirectory(solver_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_application)

set(CPACK_PACKAGE_NAME "solver")
set(CPACK_PACKAGE_VERSION "1.0.0")
set(CPACK_PACKAGE_DESCRIPTION "Quadratic equation solver")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Your Name <your-email@example.com>")

install(TARGETS solver RUNTIME DESTINATION bin)

include(CPack)
