cmake_minimum_required(VERSION 3.10...3.20)
project(FormatterInc)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# --- Настройка версии извне ---
if(NOT VERSION)
    set(VERSION "1.0.0") # Версия по умолчанию для локальной разработки
endif()

add_subdirectory(formatter_lib)
add_subdirectory(solver_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_application)


set(CPACK_PACKAGE_NAME "solver")
set(CPACK_PACKAGE_VERSION ${VERSION})
set(CPACK_PACKAGE_DESCRIPTION "Quadratic equation solver")

install(TARGETS solver RUNTIME DESTINATION bin)

include(CPack)
