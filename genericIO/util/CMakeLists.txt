project(Generic-IO-util)
cmake_minimum_required(VERSION 2.8)
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/../cpp)

link_directories( "${GENERIC_EXPORT_LIB_DIRS}")
set(UTILS Window Info)

foreach(util ${UTILS})
  ADD_EXECUTABLE(${util} ${util}.cc)
  TARGET_LINK_LIBRARIES(${util} genericCpp hypercube)
  foreach(lib ${GENERIC_EXPORT_LIBS})
    TARGET_LINK_LIBRARIES(${util} ${lib})
  endforeach(lib)
  install(TARGETS ${util} DESTINATION bin)
endforeach(util)

install(PROGRAMS ${CMAKE_CURRENT_SOURCE_DIR}/SEP2JSON DESTINATION bin)
install(PROGRAMS ${CMAKE_CURRENT_SOURCE_DIR}/JSONIZE DESTINATION bin)
