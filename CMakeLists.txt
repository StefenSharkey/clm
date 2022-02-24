cmake_minimum_required(VERSION 3.20)

project(clm VERSION 0.1)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
set(CMAKE_CPP_STANDARD 17)

set(SOURCE_LIST
    src/clm.c)

find_program(CMAKE_C_CPPCHECK NAMES cppcheck)
if (CMAKE_C_CPPCHECK)
    list(
        APPEND CMAKE_C_CPPCHECK
            "--enable=warning"
            "--inconclusive"
            "--force"
            "--inline-suppr"
    )
endif()

add_compile_options(-Wall -Wextra -Wpedantic -ggdb)

add_executable(${PROJECT_NAME} ${SOURCE_LIST})
