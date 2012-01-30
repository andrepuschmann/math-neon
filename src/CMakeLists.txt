########################################################################
# Build the library from source files
########################################################################
SET(math_neon_sources
    math_acosf.c
    math_asinf.c
    math_atan2f.c
    math_atanf.c
    math_ceilf.c
    math_cosf.c
    math_coshf.c
    math_expf.c
    math_fabsf.c
    math_floorf.c
    math_fmodf.c
    math_frexpf.c
    math_invsqrtf.c
    math_ldexpf.c
    math_log10f.c
    math_logf.c
    math_mat2.c
    math_mat3.c
    math_mat4.c
    math_modf.c
    math_powf.c
    math_runfast.c
    math_sincosf.c
    math_sinf.c
    math_sinfv.c
    math_sinhf.c
    math_sqrtf.c
    math_sqrtfv.c
    math_tanf.c
    math_tanhf.c
    math_vec2.c
    math_vec3.c
    math_vec4.c
)

set(CMAKE_CXX_COMPILER g++)
set(CMAKE_C_COMPILER  gcc)
set(CMAKE_CXX_FLAGS "-std=gnu99 -march=armv7-a -mtune=cortex-a8 -mfpu=neon -mfloat-abi=softfp")
set(CMAKE_C_FLAGS ${CMAKE_CXX_FLAGS}) #same flags for C sources

# Static library (test code can link against this)
ADD_LIBRARY(math_neon SHARED ${math_neon_sources})

########################################################################
# Add executables and link to libraries
########################################################################
ADD_EXECUTABLE (math_debug math_debug.c)
TARGET_LINK_LIBRARIES (math_debug math_neon m)
