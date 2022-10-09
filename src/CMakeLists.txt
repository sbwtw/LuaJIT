
execute_process(COMMAND ${CMAKE_C_COMPILER} -E -dM "${PROJECT_SOURCE_DIR}/src/lj_arch.h" OUTPUT_VARIABLE ARCH_DEFS)
string(REGEX MATCH "LJ_ARCH_NAME +\"([^\"]+)\"" LJ_ARCH_NAME ${ARCH_DEFS})
set(LJ_ARCH_NAME "${CMAKE_MATCH_1}")

add_subdirectory("host")



