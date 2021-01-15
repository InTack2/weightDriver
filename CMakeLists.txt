cmake_minimum_required(VERSION 2.8)

# include the project setting file
include($ENV{DEVKIT_LOCATION}/cmake/pluginEntry.cmake)

# specify project name
set(PROJECT_NAME wheghtDriver)



# set SOURCE_FILES
file(GLOB SOURCE_FILES
   ${CMAKE_SOURCE_DIR}/source/*.h
   ${CMAKE_SOURCE_DIR}/source/*.hpp
   ${CMAKE_SOURCE_DIR}/source/*.cpp
   )

# set linking libraries
set(LIBRARIES
     OpenMaya
     OpenMayaAnim
     OpenMayaRender
     OpenMayaUI
     Foundation
)

set_property( DIRECTORY PROPERTY VS_STARTUP_PROJECT ${PROJECT_NAME})

# Build plugin
build_plugin()
set_target_properties(${PROJECT_NAME} PROPERTIES VS_DEBUGGER_COMMAND "maya.exe")
set_target_properties(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/export:initializePlugin /export:uninitializePlugin")
set(CMAKE_CXX_FLAGS_DEBUG "/ZI")

