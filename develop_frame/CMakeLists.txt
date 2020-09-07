cmake_minimum_required(VERSION 3.14)

# set compiler
#set(CMAKE_C_COMPILER gcc)
set(CMAKE_CXX_COMPILER g++)

# set the project name value
set(PRO_NAME DevelopFrame)

# set the project name and version
project(${PRO_NAME} VERSION 0.1)

message(STATUS "project name: ${PRO_NAME}, version ${VERSION}")



# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

###########################################################
# add include directory
set(INCLUDE_DIRS 
    ${CMAKE_SOURCE_DIR}/include
    ${CMAKE_SOURCE_DIR}/src
    
    )
message(STATUS "set include directories: ${INCLUDE_DIRS}")
include_directories(${INCLUDE_DIRS})
###########################################################

# set configure header file
configure_file(${CMAKE_SOURCE_DIR}/include/${PRO_NAME}Config.h.in ${PRO_NAME}Config.h)
message(STATUS "set configure_file: ${PRO_NAME}Config.h")

###########################################################
# add subdirectory
set(LIB_NAME ${PRO_NAME}lib)
add_subdirectory(${CMAKE_SOURCE_DIR}/src)
###########################################################

###########################################################
#add executable
aux_source_directory(${CMAKE_SOURCE_DIR}/test EXE_SRC)
###########################################################

#link lib
link_directories(${CMAKE_SOURCE_DIR}/lib)
message(STATUS "linking lib ${LIB_NAME}")
add_executable(${PRO_NAME} ${EXE_SRC})
target_link_libraries(${PRO_NAME} PUBLIC ${LIB_NAME})


###########################################################
set(CMAKE_INSTALL_PREFIX ${CMAKE_SOURCE_DIR}/install)
install(TARGETS ${PRO_NAME} ${LIB_NAME})
install(DIRECTORY ${CMAKE_SOURCE_DIR}/include
                  ${CMAKE_SOURCE_DIR}/lib
        DESTINATION ${CMAKE_SOURCE_DIR}/install
       )
###########################################################
