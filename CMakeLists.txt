# Minimum CMake required
cmake_minimum_required(VERSION 2.8.12)

# Project
project(learn_protobuf-buffer)

# Find required protobuf package
find_package(protobuf REQUIRED)

INCLUDE_DIRECTORIES(${PROTOBUF_INCLUDE_DIR})
# 生成proto的cpp源文件和头文件
PROTOBUF_GENERATE_CPP(PROTO_SRC PROTO_HEADER addressbook.proto)
ADD_LIBRARY(proto ${PROTO_HEADER} ${PROTO_SRC})

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR})

ADD_EXECUTABLE(${CMAKE_PROJECT_NAME}_add add_person.cc)
ADD_EXECUTABLE(${CMAKE_PROJECT_NAME}_list list_people.cc)
TARGET_LINK_LIBRARIES(${CMAKE_PROJECT_NAME}_add proto ${PROTOBUF_LIBRARY})
TARGET_LINK_LIBRARIES(${CMAKE_PROJECT_NAME}_list proto ${PROTOBUF_LIBRARY})