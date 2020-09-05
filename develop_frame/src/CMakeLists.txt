message(STATUS "${CMAKE_SOURCE_DIR}/src")
aux_source_directory(${CMAKE_SOURCE_DIR}/src LIB_SRC)
message(STATUS "src: ${LIB_SRC} lib: ${LIB_NAME}")
add_library(${LIB_NAME} ${LIB_SRC})