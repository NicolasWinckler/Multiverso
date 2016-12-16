
set(INCLUDE_DIRECTORIES
	${CMAKE_SOURCE_DIR}/include/multiverso
	${ZMQ_INCLUDE_DIR}
	${MPI_CXX_INCLUDE_PATH}
	)

SET(MULTIVERSO_SERVER_SRC cl_parser.cpp main.cpp)

set(DEPENDENCIES
	pthread
	${ZMQ_LIBRARIES}
	${MPI_CXX_LIBRARIES}
)


include_directories(${INCLUDE_DIRECTORIES})
ADD_EXECUTABLE(multiverso.server ${MULTIVERSO_SERVER_SRC})

TARGET_LINK_LIBRARIES(multiverso.server ${DEPENDENCIES} multiverso)

SET_PROPERTY(TARGET multiverso.server PROPERTY CXX_STANDARD 11)

install(TARGETS multiverso.server DESTINATION bin)
