# CMAkeLists.txt file for mumpi project
cmake_minimum_required(VERSION 3.0.0)

# Options. Turn on with 'cmake -Dvarname=ON'.
set(CMAKE_BUILD_TYPE Debug)

# Project
project(klv)

# Compiler settings
if (CMAKE_VERSION VERSION_LESS "3.1")
    if (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
      set (CMAKE_CXX_FLAGS "--std=gnu++11 ${CMAKE_CXX_FLAGS}")
    endif ()
  else ()
    set (CMAKE_CXX_STANDARD 11)
endif ()
set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

# INCLUDES
include_directories(include)

# SOURCES
#Can manually add the sources using the set command as follows:
#set(SOURCES src/mainapp.cpp src/Student.cpp)
file(GLOB SOURCES "src/*.cpp")

add_library(klv SHARED ${SOURCES})

# LINKING
# target_link_libraries(libklv z) # zlib
# target_link_libraries(libklv m) # math
target_link_libraries(klv ${LOG4CPP_LIBRARIES})
