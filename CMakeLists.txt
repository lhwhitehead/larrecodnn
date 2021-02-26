# ======================================================================
#  larrecodnn main build file
#
#  cd .../path/to/build/directory
#  source .../path/to/larrecodnn/ups/setup_for_development <-d|-p>
#  buildtool [-I /install/path] -bt[i] -jN
# ======================================================================

cmake_minimum_required (VERSION 3.12...3.18 FATAL_ERROR)

project(larrecodnn LANGUAGES CXX)

# cetbuildtools contains our cmake modules
find_package(cetbuildtools REQUIRED)

list(APPEND CMAKE_MODULE_PATH $ENV{CANVAS_ROOT_IO_DIR}/Modules $ENV{ART_DIR}/Modules)

include(CetCMakeEnv)
cet_cmake_env()

cet_set_compiler_flags(DIAGS CAUTIOUS
  WERROR
  NO_UNDEFINED
#  EXTRA_FLAGS -pedantic -Wno-unused-local-typedefs
  EXTRA_FLAGS -Wno-unused-local-typedefs
)

cet_report_compiler_flags()

# these are minimum required versions, not the actual product versions
find_ups_product( larcoreobj )
find_ups_product( larcorealg )
find_ups_product( larcore )
find_ups_product( lardataobj )
find_ups_product( lardataalg )
find_ups_product( lardata )
find_ups_product( larevt )
find_ups_product( larsim )
find_ups_product( larreco )
find_ups_product( nutools )
find_ups_product( nug4 )
find_ups_product( nurandom )
find_ups_product( art )
find_ups_product(art_root_io)
find_ups_product( postgresql )
find_ups_product( range )
find_ups_product( eigen )
find_ups_product( root )

# macros for dictionary and simple_plugin
include(ArtDictionary)
include(ArtMake)
include(BuildPlugins)

if(( DEFINED ENV{TENSORFLOW_DIR} ) OR ( DEFINED ENV{TRTIS_CLIENTS_DIR} ))
  find_ups_product( protobuf )
  cet_find_library(PROTOBUF NAMES protobuf PATHS ENV PROTOBUF_LIB NO_DEFAULT_PATH )
endif ()
# tensorflow is optional
if( DEFINED ENV{TENSORFLOW_DIR} )
  # find tensorflow library
  find_ups_product( tensorflow )
  if("$ENV{TENSORFLOW_VERSION}" STREQUAL "v2_3_1")
    cet_find_library(TENSORFLOW_CC NAMES tensorflow_cc PATHS ENV TENSORFLOW_LIB NO_DEFAULT_PATH )
    cet_find_library(TENSORFLOW_FRAMEWORK NAMES tensorflow_framework PATHS ENV TENSORFLOW_LIB NO_DEFAULT_PATH )
    set(TENSORFLOW ${TENSORFLOW_CC} ${TENSORFLOW_FRAMEWORK})
  else()
    cet_find_library(TENSORFLOW NAMES tensorflow-core PATHS ENV TENSORFLOW_LIB NO_DEFAULT_PATH ) 
  endif()
endif ()
# trtis_clients is optional
if( DEFINED ENV{TRTIS_CLIENTS_DIR} )
  find_ups_product(trtis_clients)
endif ()

# source
add_subdirectory(larrecodnn)

# ups - table and config files
add_subdirectory(ups)

# packaging utility
include(UseCPack)
