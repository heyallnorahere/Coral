cmake_minimum_required(VERSION 3.21)

project(Coral)

set(CORAL_ROOT ${CMAKE_CURRENT_SOURCE_DIR})
if(${CORAL_ROOT} STREQUAL ${CMAKE_SOURCE_DIR})
    set(CORAL_STANDALONE ON)
endif()

if(${CMAKE_SYSTEM_NAME} STREQUAL "Windows")
    set(CORAL_PLAT CORAL_WINDOWS)
elseif(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
    set(CORAL_PLAT CORAL_LINUX)
elseif(${CMAKE_SYSTEM_NAME} STREQUAL "Darwin")
    set(CORAL_PLAT CORAL_MACOSX)
endif()

option(CORAL_BUILD_EXAMPLE "Build the example program." ${CORAL_STANDALONE})

add_subdirectory("Coral.Native")

if(${CORAL_BUILD_EXAMPLE})
    add_subdirectory("Example/Example.Native")
endif()
