cmake_minimum_required(VERSION 3.4.1)

project(ludimus)

set (CMAKE_CXX_STANDARD 11)

add_subdirectory(lib/curve25519)
add_subdirectory(lib/ed25519)
add_subdirectory(lib/playfair)
add_subdirectory(lib)
add_subdirectory(renderers)

add_executable( ludimus ludimus.cpp)
include_directories ( ludimus ${GST_INCLUDE_DIRS} )
target_link_libraries ( ludimus renderers airplay )
  
if(WIN32)
    target_link_libraries( ludimus -static-libgcc -static-libstdc++ -static )
endif()

install(PROGRAMS ludimus DESTINATION bin)
