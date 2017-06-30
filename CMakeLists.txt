# Minimum CMake required
cmake_minimum_required(VERSION 2.8.12)

# Project
project(learn_protobuf-buffer)

# Find required protobuf package
find_package(Protobuf REQUIRED)
include_directories(${PROTOBUF_INCLUDE_DIRS})

set(SOURCE_FILES main.cpp addressbook.pb.h addressbook.pb.cc)

include_directories(${CMAKE_CURRENT_BINARY_DIR})
PROTOBUF_GENERATE_CPP(PROTO_SRCS PROTO_HDRS addressbook.proto)
add_executable(main main.cpp ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(main ${PROTOBUF_LIBRARIES})