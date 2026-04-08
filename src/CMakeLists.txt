file(GLOB_RECURSE srcs CONFIGURE_DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
add_library(cli11 STATIC)
target_sources(cli11 PUBLIC FILE_SET CXX_MODULES FILES ${srcs})
target_include_directories(cli11 PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
include(GNUInstallDirs)
install(
    TARGETS cli11
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    CXX_MODULES_BMI DESTINATION ${CMAKE_INSTALL_LIBDIR}/cxx/bmi
)
configure_file(${CMAKE_SOURCE_DIR}/packaging/cli11.pc.in cli11.pc @ONLY)
install(
    FILES ${CMAKE_CURRENT_BINARY_DIR}/cli11.pc
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/pkgconfig
)
