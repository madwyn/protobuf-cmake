set(PROTOS
   google/protobuf/unittest_lite
   google/protobuf/unittest_import_lite
   google/protobuf/unittest_import_public_lite
   google/protobuf/unittest
   google/protobuf/unittest_custom_options
   google/protobuf/unittest_embed_optimize_for
   google/protobuf/unittest_empty
   google/protobuf/unittest_enormous_descriptor
   google/protobuf/unittest_import
   google/protobuf/unittest_import_public
   google/protobuf/unittest_lite_imports_nonlite
   google/protobuf/unittest_mset
   google/protobuf/unittest_no_generic_services
   google/protobuf/unittest_optimize_for
)

foreach(PROTO ${PROTOS})
  add_custom_command(OUTPUT ${PROTO}.pb.cc COMMAND protoc
     ARGS --cpp_out ${CMAKE_CURRENT_BINARY_DIR} -I${PROTOBUF_ROOT}/src
     ${PROTOBUF_ROOT}/src/${PROTO}.proto)
endforeach()

set(LITE_TEST_SRC 
  ${PROTOBUF_ROOT}/src/google/protobuf/lite_unittest.cc 
  ${PROTOBUF_ROOT}/src/google/protobuf/test_util_lite.cc 
  google/protobuf/unittest_import_lite.pb.cc 
  google/protobuf/unittest_import_public_lite.pb.cc
  google/protobuf/unittest_lite.pb.cc 
)

include_directories(${PROTOBUF_ROOT}/src)
include_directories(${CMAKE_CURRENT_BINARY_DIR})

add_executable(test-lite ${LITE_TEST_SRC})
target_link_libraries(test-lite libprotobuf_lite ${ZLIB_LIBRARY})
add_test(test-lite test-lite)

SET(COMMON_TEST_SRC
  ${PROTOBUF_ROOT}/src/google/protobuf/test_util.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/testing/googletest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/testing/file.cc
)

set(LAZY_TEST_SRC 
  ${COMMON_TEST_SRC}
  google/protobuf/unittest.pb.cc
  google/protobuf/unittest_import.pb.cc
  google/protobuf/unittest_import_public.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_unittest.cc
)

add_definitions(-DPROTOBUF_TEST_NO_DESCRIPTORS)
add_executable(test-lazy ${LAZY_TEST_SRC})
target_link_libraries(test-lazy libprotobuf ${ZLIB_LIBRARY})
add_test(test-lazy test-lazy)

