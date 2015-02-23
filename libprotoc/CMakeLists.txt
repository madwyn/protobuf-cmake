project( libprotoc )

include( ../protobuf-common.cmake )

append_if_exist(SOURCES
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/code_generator.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/command_line_interface.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/plugin.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/plugin.pb.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/subprocess.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/subprocess.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/zip_writer.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/zip_writer.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_enum.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_enum.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_enum_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_enum_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_extension.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_extension.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_file.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_file.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_generator.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_helpers.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_helpers.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_map_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_map_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_message.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_message.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_message_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_message_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_options.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_primitive_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_primitive_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_service.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_service.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_string_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/cpp/cpp_string_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_context.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_context.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_enum.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_enum_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_enum_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_enum.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_extension.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_extension.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_file.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_file.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_generator.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_generator_factory.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_generator_factory.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_helpers.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_helpers.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_lazy_message_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_lazy_message_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_map_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_map_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_message.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_message_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_message_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_message.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_name_resolver.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_name_resolver.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_primitive_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_primitive_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_shared_code_generator.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_shared_code_generator.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_service.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_service.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_string_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_string_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_doc_comment.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/java/java_doc_comment.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_enum.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_enum.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_enum_field.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_enum_field.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_extension.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_extension.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_field.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_field.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_file.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_file.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_generator.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_generator.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_helpers.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_helpers.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_map_field.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_map_field.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_message.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_message.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_message_field.cc
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_message_field.h
  ${PROTOBUF_ROOT}/src/google//protobuf/compiler/javanano/javanano_params.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/javanano/javanano_primitive_field.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/javanano/javanano_primitive_field.h
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/python/python_generator.cc
  ${PROTOBUF_ROOT}/src/google/protobuf/compiler/ruby/ruby_generator.cc
  )

if(WIN32 AND BUILD_SHARED_LIBS AND MSVC)
    add_definitions("-DLIBPROTOC_EXPORTS")
endif()

add_library( libprotoc ${SOURCES} )
target_link_libraries( libprotoc libprotobuf )
set_target_properties(libprotoc PROPERTIES OUTPUT_NAME "protoc")

if(WIN32 AND BUILD_SHARED_LIBS AND MSVC)
    # Install 
    install(TARGETS libprotoc
        DESTINATION ${BIN_DIR}
      )
endif()
install(TARGETS libprotoc
    DESTINATION ${LIB_DIR}
)
