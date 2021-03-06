cmake_minimum_required(VERSION 2.6)

project(IncompleteCholesky)

ADD_DEFINITIONS(-DSINGLE_PRINTER_FLAG)
ADD_DEFINITIONS(-DSINGLE_TIMER_FLAG)
ADD_DEFINITIONS(-DINFO_PRINT_FLAG)
ADD_DEFINITIONS(-DERROR_PRINT_FLAG)
ADD_DEFINITIONS(-DWARN_PRINT_FLAG)
ADD_DEFINITIONS(-DDEBUG_PRINT_FLAG)
ADD_DEFINITIONS(-DUSE_TIMER_FLAG)

find_package(CUDA REQUIRED)
if (CUDA_FOUND)
  message(STATUS "CUDA_INCLUDE_DIRS: ${CUDA_INCLUDE_DIRS}")
  message(STATUS "CUDA_VERSION     : ${CUDA_VERSION_STRING}")
  include_directories(${CUDA_INCLUDE_DIRS})
endif (CUDA_FOUND)

find_package(Eigen3 REQUIRED)
if (EIGEN3_FOUND)
  message(STATUS "EIGEN3_INCLUDE_DIRS: ${EIGEN3_INCLUDE_DIRS}")
  message(STATUS "EIGEN3_VERSION     : ${EIGEN3_VERSION_STRING}")
  include_directories(${EIGEN3_INCLUDE_DIRS})
endif (EIGEN3_FOUND)

include_directories(external)
add_subdirectory(external/mat-rbf)
add_subdirectory(src)
add_subdirectory(tests)
