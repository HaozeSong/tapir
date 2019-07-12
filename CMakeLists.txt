# Tapir
set(TAPIR_DIR ${CMAKE_CURRENT_SOURCE_DIR})
add_custom_target(lwip-tapir
  COMMAND DMTR_CFLAGS=-I${CMAKE_SOURCE_DIR}/include DMTR_LDFLAGS='-L${PROJECT_BINARY_DIR}/src/c++/libos/lwip -ldmtr-libos-lwip -Wl,-rpath,${PROJECT_BINARY_DIR}/src/c++/libos/lwip -L${CMAKE_SOURCE_DIR}/submodules/Hoard/src -lhoard -Wl,-rpath,${CMAKE_SOURCE_DIR}/submodules/Hoard/src' make
#COMMAND DMTR_CFLAGS=-I${CMAKE_SOURCE_DIR}/include DMTR_LDFLAGS='-L${PROJECT_BINARY_DIR}/libos/posix -ldmtr-libos-posix -Wl,-rpath,${PROJECT_BINARY_DIR}/libos/posix' make
  WORKING_DIRECTORY ${TAPIR_DIR}
)
add_dependencies(lwip-tapir dmtr-libos-lwip)

#
# todo: is there a way to get this to run on `make clean`?
add_custom_target(tapir-lwip-clean
    COMMAND make clean
    WORKING_DIRECTORY ${TAPIR_DIR}
)
