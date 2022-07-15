cmake_minimum_required (VERSION 3.20)

SET(TARGET_NAME "router_proto")
project(${TARGET_NAME})

include (FetchContent)
FetchContent_Declare(cmake_tool GIT_REPOSITORY https://github.com/nearmeng/cmake_tools.git GIT_TAG master)
FetchContent_MakeAvailable(cmake_tool)

fetch_content(ss_proto_common https://github.com/nearmeng/ss_proto_common.git master)

init_project()

add_library(${TARGET_NAME} INTERFACE)
add_library(mango::${TARGET_NAME} ALIAS ${TARGET_NAME})

target_include_directories(${TARGET_NAME} INTERFACE .)
target_link_libraries(${TARGET_NAME} INTERFACE mango::ss_proto_common)