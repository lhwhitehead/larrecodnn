art_make( MODULE_LIBRARIES
        larreco_RecoAlg_ImagePatternAlgs_DataProvider
	lardata_ArtDataHelper
        lardataobj_RawData
        art_Framework_Services_System_TriggerNamesService_service
        larsim_MCCheater_ParticleInventoryService_service
                       larreco_Calorimetry
                       larcorealg_Geometry
                       lardataalg_DetectorInfo
                       lardataobj_RecoBase
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
                       ${ROOT_BASIC_LIB_LIST}
                       ROOT::Core
)

install_headers()
install_fhicl()
install_source()
