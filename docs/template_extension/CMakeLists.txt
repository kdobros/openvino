# Copyright (C) 2020 Intel Corporation
# SPDX-License-Identifier: Apache-2.0
#

# [cmake:extension]
set(TARGET_NAME "template_extension")

find_package(ngraph REQUIRED)
find_package(InferenceEngine REQUIRED)

file(GLOB_RECURSE SRC *.cpp)

add_library(${TARGET_NAME} SHARED ${SRC})

target_compile_definitions(${TARGET_NAME} PRIVATE IMPLEMENT_INFERENCE_EXTENSION_API)
target_link_libraries(${TARGET_NAME} PRIVATE ${InferenceEngine_LIBRARIES}
                                             ${NGRAPH_LIBRARIES})
# [cmake:extension]
