cmake_minimum_required (VERSION 2.8.11)
project (necpp)

if(WIN32)
  message("Windows configuration")
  configure_file( ${CMAKE_CURRENT_SOURCE_DIR}/win32/nec2++/config.h ${CMAKE_CURRENT_SOURCE_DIR}/src COPYONLY )
  set( CMAKE_CXX_FLAGS "-DWIN32 -DNEC_ERROR_CHECK=1" )
  if(MSVC)
    set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} " /EHsc")
  endif(MSVC)
endif(WIN32)

add_subdirectory (src)
