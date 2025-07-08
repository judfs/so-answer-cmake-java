#      ██╗ █████╗ ██╗   ██╗ █████╗ 
#      ██║██╔══██╗██║   ██║██╔══██╗
#      ██║███████║██║   ██║███████║
# ██   ██║██╔══██║╚██╗ ██╔╝██╔══██║
# ╚█████╔╝██║  ██║ ╚████╔╝ ██║  ██║
#  ╚════╝ ╚═╝  ╚═╝  ╚═══╝  ╚═╝  ╚═╝
                                 

include(UseJava)

set(top_package com)
set(java_src 
    com/example/Hello.java
)
set(java_main com/example/Hello)
set(jar_name example-hello)
set(jar_name_sources ${jar_name}-sources)
set(sources_jar ${jar_name_sources}.jar)

add_jar(example-java
    SOURCES ${java_src}
    OUTPUT_NAME ${jar_name}
    ENTRY_POINT ${java_main}
)

install_jar(example-java DESTINATION share/java)


# Make a sources jar.
add_custom_command(
    OUTPUT 
        "${sources_jar}"
    COMMAND 
        # -- Long options are not supported on all java distributions.
        # -- ${Java_JAR_EXECUTABLE} --create --file "${sources_jar}" -C ${CMAKE_CURRENT_SOURCE_DIR} ${top_package}
        ${Java_JAR_EXECUTABLE} cf "${CMAKE_CURRENT_BINARY_DIR}/${sources_jar}" ${top_package}
    WORKING_DIRECTORY
        "${CMAKE_CURRENT_SOURCE_DIR}"
    DEPENDS 
        ${java_src}
    VERBATIM
    COMMENT 
        "Creating sources jar"
)

add_custom_target(example-java-src
    DEPENDS "${sources_jar}"
)
add_dependencies(example-java example-java-src)

install(FILES "${CMAKE_CURRENT_BINARY_DIR}/${sources_jar}" DESTINATION share/java)
