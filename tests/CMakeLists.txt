find_package(GTest REQUIRED)

include_directories(${GTEST_INCLUDE_DIRS})

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
   google/protobuf/compiler/cpp/cpp_test_bad_identifiers
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


set(COMMON_TEST_SRC
  ${PROTOBUF_ROOT}/src/google/protobuf/test_util.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/testing/googletest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/testing/file.cc
)

set(PROTOBUF_TEST_SRC
  ${COMMON_TEST_SRC}
  ${PROTOBUF_ROOT}/src/google/protobuf/stubs/common_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/stubs/once_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/stubs/strutil_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/stubs/structurally_valid_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/stubs/stringprintf_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/stubs/template_util_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/stubs/type_traits_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/descriptor_database_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/descriptor_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/dynamic_message_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/extension_set_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/generated_message_reflection_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/message_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/reflection_ops_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/repeated_field_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/repeated_field_reflection_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/text_format_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/unknown_field_set_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/wire_format_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/io/coded_stream_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/io/printer_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/io/tokenizer_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/io/zero_copy_stream_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/command_line_interface_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/importer_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/mock_code_generator.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/parser_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_bootstrap_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_unittest.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_plugin_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_plugin_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_doc_comment_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/python/python_plugin_unittest.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/unittest.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/unittest_custom_options.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/unittest_import.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/unittest_import_public.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/unittest_mset.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_test_bad_identifiers.pb.cc
)

set(LAZY_TEST_SRC 
  ${COMMON_TEST_SRC}
  google/protobuf/unittest.pb.cc
  google/protobuf/unittest_import.pb.cc
  google/protobuf/unittest_import_public.pb.cc
  google/protobuf/unittest_optimize_for.pb.cc
  google/protobuf/unittest_embed_optimize_for.pb.cc
  google/protobuf/unittest_no_generic_services.pb.cc
  google/protobuf/compiler/cpp/cpp_test_bad_identifiers.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_unittest.cc
)

add_executable(test-protobuf ${PROTOBUF_TEST_SRC})
target_link_libraries(test-protobuf libprotobuf libprotoc ${GTEST_BOTH_LIBRARIES} ${ZLIB_LIBRARY})
add_test(test-protobuf test-protobuf WORKING_DIRECTORY ${PROTOBUF_ROOT})

add_executable(test-lite ${LITE_TEST_SRC})
target_link_libraries(test-lite libprotobuf_lite ${ZLIB_LIBRARY})
add_test(test-lite test-lite WORKING_DIRECTORY ${PROTOBUF_ROOT})

add_definitions(-DPROTOBUF_TEST_NO_DESCRIPTORS)
add_executable(test-lazy ${LAZY_TEST_SRC})
target_link_libraries(test-lazy libprotobuf libprotoc ${GTEST_BOTH_LIBRARIES} ${ZLIB_LIBRARY})
add_test(test-lazy test-lazy WORKING_DIRECTORY ${PROTOBUF_ROOT})

