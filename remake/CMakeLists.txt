cmake_minimum_required(VERSION 3.10)

project(Plazza)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(SOURCES
    src/main.cpp
    src/Kitchen.cpp
    src/Order.cpp
    src/Restaurant.cpp
    src/IPC.cpp
)

include_directories(include)

add_executable(plazza ${SOURCES})

if (WIN32)
    target_link_libraries(plazza ws2_32)
else()
    target_link_libraries(plazza pthread)
endif()

if (CMAKE_CXX_COMPILER_ID STREQUAL "GNU" OR CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
    target_compile_options(plazza PRIVATE -Wall -Wextra -Wpedantic)
endif()

install(TARGETS plazza DESTINATION bin)
