cmake_minimum_required(VERSION 3.10...3.20)
project(FormatterInc)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


if(NOT VERSION)
    set(VERSION "1.0.0")
endif()

add_subdirectory(formatter_lib)
add_subdirectory(solver_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_application)

set(CPACK_PACKAGE_NAME "solver")
set(CPACK_PACKAGE_VERSION ${VERSION})
set(CPACK_PACKAGE_DESCRIPTION "Quadratic equation solver")

set(CPACK_PACKAGE_CONTACT "ivananisimov2121@gmail.com")

set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Ivan Anisimov ivananisimov2121@gmail.com")

install(TARGETS solver RUNTIME DESTINATION bin)

include(CPack)
