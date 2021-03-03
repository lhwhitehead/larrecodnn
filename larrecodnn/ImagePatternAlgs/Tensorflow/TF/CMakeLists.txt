include_directories( $ENV{TENSORFLOW_INC}/absl )
art_make(
          LIB_LIBRARIES
			${FHICLCPP}
			cetlib cetlib_except
			${TENSORFLOW}
			${PROTOBUF}
			${FOR_TENSORFLOW}
      #rt #workaround for larsoft issue 17960
        )

cet_remove_compiler_flags(CXX -pedantic)

install_headers()
install_source()

