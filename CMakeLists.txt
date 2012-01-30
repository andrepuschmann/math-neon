########################################################################
# Prevent in-tree builds
########################################################################
IF(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR})
    MESSAGE(FATAL_ERROR "Prevented in-tree built. This is bad practice.")
ENDIF(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR})

########################################################################
# Project setup
#######################################################################
CMAKE_MINIMUM_REQUIRED (VERSION 2.6)
PROJECT (NEON_MATH)
ENABLE_TESTING()
LIST(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake/modules")

ADD_SUBDIRECTORY (src)

# Make sure the compiler can find include files
include_directories (${NEON_MATH_SOURCE_DIR}/src) 

# Make sure the linker can find the library once it is built. 
link_directories (${NEON_MATH_BINARY_DIR}/src) 

