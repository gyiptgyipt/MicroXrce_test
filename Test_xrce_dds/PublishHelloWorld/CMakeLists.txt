# Minimum CMake version required
cmake_minimum_required(VERSION 3.5)

# Project name and languages
project(PublishHelloWorld C)

# Set the C standard version
set(CMAKE_C_STANDARD 99)

# Find and include the required Micro XRCE-DDS client package
find_package(microxrcedds_client REQUIRED)

# Include the directories for the project
include_directories(
    include
    ${MICROXRCEDDS_CLIENT_INCLUDE_DIRS}
)

# # Generate code from the IDL file using microxrceddsgen
# add_custom_command(
#     OUTPUT /home/zyme/Test_xrce_dds/PublishHelloWorld/src/HelloWorld.c `/include/HelloWorld.h
#     #COMMAND microxrceddsgen -d ${CMAKE_BINARY_DIR} -language c ${CMAKE_SOURCE_DIR}/HelloWorld.idl
#     DEPENDS ${CMAKE_SOURCE_DIR}/HelloWorld.idl
#     COMMENT "Generating code from IDL file"
# )

# Add the generated source and header files to the project
add_executable(helloworld_xrce
    src/main.c
    src/HelloWorld.c
)

# Link the executable with the Micro XRCE-DDS client library
target_link_libraries(helloworld_xrce
    microxrcedds_client
)
