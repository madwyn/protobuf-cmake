protobuf-cmake: CMake build files for Protocol Buffers

This a fork from the original work of Jesper Eskilson (jesper@eskilson.se) with contributions from several other people.

This CMake project will try to keep up with the latest Protobuf. In this case, the latest build scripts may not work well with older versions of Protobuf. However, you can pull an older version corresponding to the specific Protobuf release

Requirements
------------

* CMake version 2.6
* Protobuf version 3.0.0-alpha-1

Download links
--------------
http://www.cmake.org/cmake/resources/software.html
https://github.com/google/protobuf/releases

Instructions
------------

On Unix, the Protobuf configure script needs to be run before running 
CMake in order to create the config.h file:

   $ cd /path/to/protobuf
   $ ./configure

The CMake variable PROTOBUF_ROOT needs to be set to the location of
the Protocol Buffers sources. When running CMake on the command line,
this can be set like this:

   $ cd build
   $ cmake /path/to/protobuf-cmake -DPROTOBUF_ROOT=/path/to/protobufs
