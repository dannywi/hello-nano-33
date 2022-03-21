cmake_minimum_required(VERSION 3.16)
set(CMAKE_CXX_STANDARD 14)

# TEST EXECUTABLE
project(hello-test)
add_executable(${PROJECT_NAME}
  sine-model-test.cpp
)

# ADD INCLUDE FILES
target_include_directories(${PROJECT_NAME} PUBLIC
  ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/
)

# ADD MICRO LIBRARY
add_library(micro
  ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/tensorflow/lite/micro/micro_error_reporter.cc
  ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/tensorflow/lite/micro/debug_log.cc
  ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/tensorflow/lite/micro/micro_string.cc
  ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/tensorflow/lite/micro/system_setup.cc
)

target_include_directories(micro PUBLIC
  ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/
)

target_link_libraries(${PROJECT_NAME} PUBLIC micro)

# ADD SCHEMA LIBRARY
# add_library(micro
#   ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/tensorflow/lite/schema/schema_generated.h
# )

# target_include_directories(micro PUBLIC
#   ${PROJECT_SOURCE_DIR}/../lib/tflite-micro/
# )

# target_link_libraries(${PROJECT_NAME} PUBLIC micro)