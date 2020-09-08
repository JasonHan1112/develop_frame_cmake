message(STATUS "${CMAKE_SOURCE_DIR}/src")
aux_source_directory(${CMAKE_SOURCE_DIR}/src LIB_SRC)
message(STATUS "src: ${LIB_SRC} lib: ${SRC_LIB_NAME}")
add_library(${SRC_LIB_NAME} ${LIB_SRC})
