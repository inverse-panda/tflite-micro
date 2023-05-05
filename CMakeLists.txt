file(GLOB_RECURSE tflite_lib_files
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/*.cc  
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/*.c 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/*.h
    )

list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/arc_custom
    )
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/arc_emsdp
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/benchmarks
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/bluepill
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/ceva
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/chre
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/cortex_m_corstone_300
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/cortex_m_generic
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/examples
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/hexagon
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/integration_tests
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/kernels/arc_mli
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/kernels/ceva
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/kernels/cmsis_nn
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/kernels/ethos_u
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/kernels/xtensa
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/experimental
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/memory_arena_threshold_test.cc
)
list(FILTER tflite_lib_files EXCLUDE REGEX 
    ${CMAKE_CURRENT_SOURCE_DIR}/tensorflow/lite/micro/python
)

file(GLOB kiss_fft  
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/kissfft/iss_fft.c
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/kissfft/tools/kiss_fftr.c
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/kissfft/_kiss_fft_guts.h
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/kissfft/kiss_fft.h
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/kissfft/tools/kiss_fftr.h
    )

file(GLOB gemmlowp  
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/gemmlowp/fixedpoint/*.h
    ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/gemmlowp/internal/*.h
    )

add_library(tflite_lib ${tflite_lib_files} ${kiss_fft} ${gemmlowp})
target_include_directories(tflite_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(tflite_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/flatbuffers/include)
target_include_directories(tflite_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/gemmlowp)
target_include_directories(tflite_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/kissfft/tools)
target_include_directories(tflite_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/kissfft)
target_include_directories(tflite_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/third_party_submodules/ruy)