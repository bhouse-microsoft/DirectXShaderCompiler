# Copyright (C) Microsoft Corporation. All rights reserved.
# This file is distributed under the University of Illinois Open Source License. See LICENSE.TXT for details.

if (WIN32)
  find_package(DiaSDK REQUIRED) # Used for constants and declarations.
endif (WIN32)

add_llvm_library(LLVMDxilDia
  dxcdia.cpp

  ADDITIONAL_HEADER_DIRS
  ${LLVM_MAIN_INCLUDE_DIR}/llvm/IR
)

if (WIN32)
  target_link_libraries(LLVMDxilDia PRIVATE ${LIBRARIES} ${DIASDK_LIBRARIES})
  include_directories(AFTER ${LLVM_INCLUDE_DIR}/dxc/Tracing ${DIASDK_INCLUDE_DIRS})
endif (WIN32)
