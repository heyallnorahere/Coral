cmake_minimum_required(VERSION 3.21)

file(GLOB_RECURSE CORAL_SRC CONFIGURE_DEPENDS
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h*"
    "${CMAKE_CURRENT_SOURCE_DIR}/*.c*"
)

add_library(Coral.Native STATIC ${CORAL_SRC})
target_precompile_headers(Coral.Native PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/Source/CoralPCH.hpp")
target_compile_definitions(Coral.Native PUBLIC ${CORAL_PLAT})

set_target_properties(Coral.Native PROPERTIES
    CXX_STANDARD 20
)

target_include_directories(Coral.Native
    PUBLIC
    "${CMAKE_CURRENT_SOURCE_DIR}/Include"
    PRIVATE
    "${CMAKE_CURRENT_SOURCE_DIR}/Source"
    "${CORAL_ROOT}/NetCore"
)
