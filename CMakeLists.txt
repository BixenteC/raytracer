cmake_minimum_required(VERSION 3.1..0...3.27.0)
project(raytracer VERSION 0.1.0 LANGUAGES C CXX)

# Set to C++11
set ( CMAKE_CXX_STANDARD          11 )
set ( CMAKE_CXX_STANDARD_REQUIRED ON )
set ( CMAKE_CXX_EXTENSIONS        OFF )

include(CTest)
enable_testing()

set ( SOURCE_ONE_WEEKEND
  src/InOneWeekend/vec3.h
  src/InOneWeekend/color.h
  src/InOneWeekend/ray.h
  src/InOneWeekend/sphere.h
  src/InOneWeekend/hittable.h
  src/InOneWeekend/hittable_list.h
  src/InOneWeekend/rtweekend.h
  src/InOneWeekend/camera.h
  src/InOneWeekend/material.h

  src/InOneWeekend/main.cpp
)

include_directories(src)

# Compiler flags
add_compile_options(-Wnon-virtual-dtor) # Class has virtual functions, but its destructor is not virtual
add_compile_options(-Wreorder) # Data member will be initialized after [other] data member
add_compile_options(-Wmaybe-uninitialized) # Variable improperly initialized
add_compile_options(-Wunused-variable) # Variable is defined but unused

# Executables
add_executable(inOneWeekend      ${EXTERNAL} ${SOURCE_ONE_WEEKEND})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
