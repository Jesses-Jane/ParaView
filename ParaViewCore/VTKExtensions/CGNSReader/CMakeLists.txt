# -----------------------------------------------------------------------------
# Disable some warnings
# -----------------------------------------------------------------------------
if (WIN32)
  if (MSVC_VERSION GREATER 1400)
    # -------------------------------------------------------------------------
    # Disable deprecation warnings for standard C and STL functions in VS2005
    # and newer
    # -------------------------------------------------------------------------
    add_definitions(-D_CRT_SECURE_NO_DEPRECATE)
  endif ()
endif()

set(Module_SRCS
  cgio_helpers.cxx
  vtkCGNSFileSeriesReader.cxx
  vtkCGNSReader.cxx
  vtkCGNSReaderInternal.cxx
  vtkCGNSSubsetInclusionLattice.cxx
  vtkFileSeriesHelper.cxx
  vtkCGNSCache.h
  )

set_source_files_properties(
  cgio_helpers
  vtkCGNSReaderInternal
  vtkFileSeriesHelper
  vtkCGNSCache
  PROPERTIES
    SKIP_HEADER_INSTALL 1
)

vtk_module_library(vtkPVVTKExtensionsCGNSReader ${Module_SRCS})
