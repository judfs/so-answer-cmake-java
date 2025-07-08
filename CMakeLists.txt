# ██████╗  ██████╗  ██████╗ ████████╗
# ██╔══██╗██╔═══██╗██╔═══██╗╚══██╔══╝
# ██████╔╝██║   ██║██║   ██║   ██║   
# ██╔══██╗██║   ██║██║   ██║   ██║   
# ██║  ██║╚██████╔╝╚██████╔╝   ██║   
# ╚═╝  ╚═╝ ╚═════╝  ╚═════╝    ╚═╝   
                                   

cmake_minimum_required(VERSION 3.15)

project(example_with_java)

find_package(Java)

add_subdirectory(example-cpp)

if(${Java_FOUND})
    add_subdirectory(example-java)
else()
    message(STATUS "Java support not enabled.")
endif()
