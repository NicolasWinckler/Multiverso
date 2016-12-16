cmake_minimum_required(VERSION 3.1)

PROJECT(MULTIVERSO)

# set cmake Find_package path
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake/modules" ${CMAKE_MODULE_PATH})

# Default zmq/mpi prefix
SET(THIRD_PARTY ${PROJECT_SOURCE_DIR}/third_party)

# if MPI_CXX_COMPILER defined use the specified path otherwise use the default zmq/mpi prefix
if(NOT MPI_CXX_COMPILER)
	set(MPI_CXX_COMPILER "${THIRD_PARTY}/bin/mpicxx")
endif(NOT MPI_CXX_COMPILER)

# if USE_ZMQ_PATH defined use the specified path otherwise use the default zmq/mpi prefix
if(NOT USE_ZMQ_PATH)
	set(USE_ZMQ_PATH "${THIRD_PARTY}")
endif(NOT USE_ZMQ_PATH)

# find packages
FIND_PACKAGE(Threads REQUIRED)
FIND_PACKAGE(ZeroMQ 4.1.3 REQUIRED)
FIND_PACKAGE(MPI REQUIRED)

# c++ flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC -Wall -std=c++11 -O3")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-sign-compare -fno-omit-frame-pointer -fpermissive")

ADD_SUBDIRECTORY(src)

