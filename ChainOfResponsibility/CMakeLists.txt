SET(MODULE_NAME "ChainOfResponsibility")
SET(MODULE_DIRECTORY "ChainOfResponsibility")

set(CMAKE_C_COMPILER /usr/bin/gcc)
set(CMAKE_CXX_COMPILER /usr/bin/g++)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# including source code
set(PROJECT_SOURCE_DIR ${CMAKE_HOME_DIRECTORY}/${MODULE_DIRECTORY}/src)
set(PROJECT_INCLUDE_DIR ${CMAKE_HOME_DIRECTORY}/${MODULE_DIRECTORY}/include)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_HOME_DIRECTORY}/${MODULE_DIRECTORY}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_HOME_DIRECTORY}/${MODULE_DIRECTORY}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_HOME_DIRECTORY}/${MODULE_DIRECTORY}/bin)

file(GLOB CHAIN_OF_REPONSIBILITY_SOURCE_FILES_TOP "${PROJECT_SOURCE_DIR}/${MODULE_DIRECTORY}/*.cpp")
file(GLOB_RECURSE CHAIN_OF_REPONSIBILITY_SOURCE_FILES_NESTED ${PROJECT_SOURCE_DIR}/${MODULE_DIRECTORY}/*.cpp)
set(CHAIN_OF_REPONSIBILITY_SOURCE_FILES
    ${CHAIN_OF_REPONSIBILITY_SOURCE_FILES_TOP}
    ${CHAIN_OF_REPONSIBILITY_SOURCE_FILES_NESTED}
)

include_directories("${PROJECT_INCLUDE_DIR}")
include_directories("${PROJECT_SOURCE_DIR}")

add_library(${MODULE_NAME} SHARED ${CHAIN_OF_REPONSIBILITY_SOURCE_FILES})
target_include_directories(${MODULE_NAME} PUBLIC ${PROJECT_INCLUDE_DIR})

add_executable(ChainOfResponsibilityPattern ${PROJECT_SOURCE_DIR}/main.cpp)
target_link_libraries(ChainOfResponsibilityPattern ${MODULE_NAME})
