include_directories( $ENV{TENSORFLOW_INC}/absl )

art_make(
          TOOL_LIBRARIES
          larreco_RecoAlg_ImagePatternAlgs_DataProvider
          larrecodnn_ImagePatternAlgs_Tensorflow_TF
          ROOT::Core
          canvas
          ${MF_MESSAGELOGGER}
        )

cet_remove_compiler_flags(CXX -pedantic)

install_source()
