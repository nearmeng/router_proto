cmake_minimum_required (VERSION 3.20)

SET(TARGET_NAME "router_proto")
project(${TARGET_NAME})

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include (fetch_content)
fetch_content(ss_proto_common https://github.com/nearmeng/ss_proto_common.git master)

add_library(${TARGET_NAME} INTERFACE)
add_library(mango::${TARGET_NAME} ALIAS ${TARGET_NAME})

target_include_directories(${TARGET_NAME} INTERFACE .)
target_link_libraries(${TARGET_NAME} INTERFACE mango::ss_proto_common)