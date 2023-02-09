# Created by Hans to verify local created examples
# Time: 2023/01/13 16:50
# Author: Hans Sun

set(LOCAL_EXAMPLES_SRCS)
list(APPEND LOCAL_EXAMPLES_SRCS
  poisson.cpp
  elas_beam.cpp
  hyper_elas_beam.cpp
)

# Include the source directory where mfem.hpp and mfem-performance.hpp are.
include_directories(BEFORE ${PROJECT_BINARY_DIR})

# Add "test_locals" target, see below.
add_custom_target(test_local
  ${CMAKE_CTEST_COMMAND} -R local USES_TERMINAL)

# Add one executable per cpp file, adding "locals_" as prefix. Sets
# "test_locals" as a target that depends on the given examples.
set(PFX local_)
add_mfem_examples(LOCAL_EXAMPLES_SRCS ${PFX} "" test_local)