#
# This file is a part of Stand-alone Future Library (safl).
#

option(SAFL_DEVELOPER "Enable the developer mode" ON)

find_package(Doxygen)
if(NOT DOXYGEN_FOUND)
    return()
endif()

find_program(QHELPGENERATOR_EXECUTABLE
  NAMES
    qhelpgenerator
    qhelpgenerator-qt5
)
if(QHELPGENERATOR_EXECUTABLE)
    set(SAFL_DOXY_GENERATE_QHP YES)
    set(SAFL_DOXY_QHG_LOCATION ${QHELPGENERATOR_EXECUTABLE})
endif()

if(SAFL_DEVELOPER)
    set(SAFL_DOXY_INTERNAL_DOCS YES)
endif()

configure_file(Doxyfile.in Doxyfile @ONLY)
add_custom_target(doc
  COMMAND
    ${DOXYGEN_EXECUTABLE} Doxyfile
  WORKING_DIRECTORY
    ${CMAKE_CURRENT_BINARY_DIR}
  SOURCES
    SaflDoxygen.css
    pages/MainPage.dox
    pages/Specification.dox
  COMMENT
    "Generating SAFL documentation"
  VERBATIM
)
