include_directories(${CMAKE_SOURCE_DIR})
add_executable(thdat thdat.c)
find_package(OpenMP)
if (OPENMP_FOUND)
  set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
  set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
endif()
target_link_libraries(thdat thtk util)
link_setargv(thdat)
install(TARGETS thdat DESTINATION bin)
install(FILES thdat.1 DESTINATION share/man/man1)
