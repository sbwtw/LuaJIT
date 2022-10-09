
add_executable(minilua minilua.c)

if (NOT MSVC)
    target_link_libraries(minilua m)
endif()

set(DYNASM "${PROJECT_SOURCE_DIR}/dynasm/dynasm.lua")
set(ARGS "-D" "ENDIAN_LE" "-D" "P64" "-D" "JIT" "-D" "FFI" "-D" "FPU" "-D" "HFABI" "-D" "VER=" "-o" "buildvm_arch.h" "${PROJECT_SOURCE_DIR}/src/vm_${LJ_ARCH_NAME}.dasc")
add_custom_command(OUTPUT buildvm_arch COMMAND minilua ${DYNASM} ${ARGS} DEPENDS minilua)

add_custom_target(run ALL DEPENDS buildvm_arch)
