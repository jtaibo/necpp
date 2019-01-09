cmake_minimum_required (VERSION 2.8.11)
project (necpp)

set( CMAKE_CXX_FLAGS "-DWIN32 -DNEC_ERROR_CHECK=1" )

add_subdirectory (src)
