cmake_minimum_required(VERSION 3.15)

project(main)

# 清除缓存
execute_process(COMMAND ${CMAKE_COMMAND} -E remove_directory ${CMAKE_BINARY_DIR}/CMakeFiles)
execute_process(COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_BINARY_DIR}/CMakeCache.txt)

add_compile_options(-finput-charset=UTF-8 -fexec-charset=UTF-8)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

# 使用 aux_source_directory 查找源文件
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)
aux_source_directory(${PROJECT_SOURCE_DIR}/include SRC_LIST2)

# 合并 SRC_LIST 和 SRC_LIST2
list(APPEND SRC_LIST ${SRC_LIST2})

include_directories(${PROJECT_SOURCE_DIR}/include)

add_executable(main ${SRC_LIST})
