project(vtkSlicer${MODULE_NAME}ModuleLogic)

#
# See CMake/SlicerMacroBuildModuleLogic.cmake for details
#

set(KIT ${PROJECT_NAME})

# The header '${module_logic_name}Export.h' will be automatically configured.
set(${KIT}_EXPORT_DIRECTIVE "VTK_SLICER_${MODULE_NAME_UPPER}_MODULE_LOGIC_EXPORT")

# Additional directories to include
set(${KIT}_INCLUDE_DIRECTORIES
    ${Slicer_INSTALL_QTLOADABLEMODULES_INCLUDE_DIR}/vtkSlicerMarkupsModuleMRML
    ${Slicer_INSTALL_QTLOADABLEMODULES_INCLUDE_DIR}/vtkSlicerAnnotationsModuleMRML
  )

# Source files
set(${KIT}_SRCS
  vtkSlicer${MODULE_NAME}Logic.cxx
  vtkSlicer${MODULE_NAME}Logic.h
  )

  # Additional Target libraries
set(${KIT}_TARGET_LIBRARIES
  vtkSlicerAnnotationsModuleMRML
  vtkSlicerMarkupsModuleMRML
  ${ITK_LIBRARIES}
  )

link_directories(${Slicer_INSTALL_QTLOADABLEMODULES_LIB_DIR})

#-----------------------------------------------------------------------------
SlicerMacroBuildModuleLogic(
  NAME ${KIT}
  EXPORT_DIRECTIVE ${${KIT}_EXPORT_DIRECTIVE}
  INCLUDE_DIRECTORIES ${${KIT}_INCLUDE_DIRECTORIES}
  SRCS ${${KIT}_SRCS}
  TARGET_LIBRARIES ${${KIT}_TARGET_LIBRARIES}
  )
