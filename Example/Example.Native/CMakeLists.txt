cmake_minimum_required(VERSION 3.21)

file(GLOB_RECURSE EXAMPLE_SRC CONFIGURE_DEPENDS
    "${CMAKE_CURRENT_SOURCE_DIR}/Source/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/Source/*.hpp"
)

add_executable(Example.Native ${EXAMPLE_SRC})
target_link_libraries(Example.Native PRIVATE Coral.Native)

set_target_properties(Example.Native PROPERTIES
    CXX_STANDARD 20
)
