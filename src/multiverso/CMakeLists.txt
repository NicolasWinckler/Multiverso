INCLUDE_DIRECTORIES(
	${ZMQ_INCLUDE_DIR}
	${MPI_CXX_INCLUDE_PATH}
	${CMAKE_SOURCE_DIR}/include
	)


SET(MULTIVERSO_SRC multiverso.cpp aggregator.cpp  endpoint_list.cpp   stop_watch.cpp zmq_util.cpp barrier.cpp lock.cpp parameter_loader.cpp  table.cpp communicator.cpp  log.cpp  row.cpp  table_iter.cpp data_block.cpp    mpi_util.cpp  row_iter.cpp trainer.cpp delta_pool.cpp  msg_pack.cpp  server.cpp vector_clock.cpp
)
SET(MULTIVERSO_HDR multiverso.h aggregator.h  endpoint_list.h   stop_watch.h zmq_util.h barrier.h lock.h parameter_loader.h  table.h communicator.h  log.h  row.h  table_iter.h data_block.h    mpi_util.h  row_iter.h trainer.h delta_pool.h  msg_pack.h  server.h vector_clock.h
)


LINK_DIRECTORIES(${THIRD_PARTY_LIB})

ADD_LIBRARY(multiverso ${MULTIVERSO_SRC})
#Add_Library(multiverso SHARED ${SRCS})
#Add_Library(multiverso_static STATIC ${SRCS})

TARGET_LINK_LIBRARIES(multiverso mpich mpl zmq pthread)
TARGET_LINK_LIBRARIES(multiverso_static mpich mpl zmq pthread)

SET_PROPERTY(TARGET multiverso PROPERTY CXX_STANDARD 11)



install(TARGETS multiverso DESTINATION lib)
install(TARGETS multiverso_static DESTINATION lib)
install(FILES ${MULTIVERSO_HDR} DESTINATION include)








include_directories(${INCLUDE_DIRECTORIES})
Add_Library(${LIBRARY_NAME} SHARED ${SRCS})
Add_Library(${LIBRARY_NAME}_static STATIC ${SRCS})
target_link_libraries(${LIBRARY_NAME} ${DEPENDENCIES})
target_link_libraries(${LIBRARY_NAME}_static ${DEPENDENCIES})

