cmake_minimum_required(VERSION 2.8.18)
project(METIS C)

set(SHARED FALSE CACHE BOOL "build a shared library")

if(MSVC)
  set(METIS_INSTALL FALSE)
else()
  set(METIS_INSTALL TRUE)
endif()

# Configure libmetis library.
if(SHARED)
  set(METIS_LIBRARY_TYPE SHARED)
else()
  set(METIS_LIBRARY_TYPE STATIC)
endif(SHARED)

include(./conf/gkbuild.cmake)
add_subdirectory("libmetis")

target_include_directories(${PROJECT_NAME} PRIVATE ${GKLIB_DIR})
target_include_directories(${PROJECT_NAME} PRIVATE ${METIS_DIR}/include)
