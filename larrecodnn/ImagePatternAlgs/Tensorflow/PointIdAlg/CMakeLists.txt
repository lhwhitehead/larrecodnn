include_directories($ENV{TENSORFLOW_INC}/absl)

art_make(LIB_LIBRARIES larreco_RecoAlg_ImagePatternAlgs_DataProvider
                       larrecodnn_ImagePatternAlgs_Keras
                       larrecodnn_ImagePatternAlgs_Tensorflow_TF
                       larcore_Geometry_Geometry_service
                       larcorealg_Geometry
                       lardataalg_DetectorInfo
                       lardataobj_RecoBase
                       larreco_Calorimetry
                       nusimdata_SimulationBase
                       ${ART_FRAMEWORK_CORE}
                       ${ART_FRAMEWORK_PRINCIPAL}
                       ${ART_FRAMEWORK_SERVICES_REGISTRY}
                       ${ART_ROOT_IO_TFILE_SUPPORT}
                       ${ART_ROOT_IO_TFILESERVICE_SERVICE}
                       ${ART_FRAMEWORK_SERVICES_OPTIONAL_RANDOMNUMBERGENERATOR_SERVICE}
                       art_Persistency_Common
                       art_Persistency_Provenance
                       art_Utilities
                       canvas
                       ${MF_MESSAGELOGGER}
                       ${TRTIS_CLIENTS_LIBRARY}
                       ${FHICLCPP}
                       cetlib cetlib_except
                       ${CLHEP}
                       ${ROOT_BASIC_LIB_LIST}
                       ROOT::Core
                       ROOT::Minuit
                       ROOT::Minuit2
        )

cet_remove_compiler_flags(CXX -pedantic)

install_headers()
install_fhicl()
install_source()
