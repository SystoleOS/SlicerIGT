project(vtkSlicer${MODULE_NAME}ModuleMRML)

set(KIT ${PROJECT_NAME})

set(${KIT}_EXPORT_DIRECTIVE "VTK_SLICER_${MODULE_NAME_UPPER}_MODULE_MRML_EXPORT")

set(${KIT}_INCLUDE_DIRECTORIES
  ${VTKVOLUMERECONSTRUCTION_INCLUDE_DIRS}
  ${Slicer_INSTALL_QTLOADABLEMODULES_INCLUDE_DIR}/vtkSlicerAnnotationsModuleMRML
  ${Slicer_INSTALL_QTLOADABLEMODULES_INCLUDE_DIR}/vtkSlicerMarkupsModuleMRML
  ${Slicer_INSTALL_QTLOADABLEMODULES_INCLUDE_DIR}/vtkSlicerSequencesModuleMRML
  )

set(${KIT}_SRCS
  vtkMRML${MODULE_NAME}Node.cxx
  vtkMRML${MODULE_NAME}Node.h
  )

set(${KIT}_TARGET_LIBRARIES
  ${MRML_LIBRARIES}
  vtkSlicerSequencesModuleMRML
  vtkVolumeReconstruction
  vtkSlicerAnnotationsModuleMRML
  )

link_directories(${Slicer_INSTALL_QTLOADABLEMODULES_LIB_DIR})

# --------------------------------------------------------------------------
SlicerMacroBuildModuleMRML(
  NAME ${KIT}
  EXPORT_DIRECTIVE ${${KIT}_EXPORT_DIRECTIVE}
  INCLUDE_DIRECTORIES ${${KIT}_INCLUDE_DIRECTORIES}
  SRCS ${${KIT}_SRCS}
  TARGET_LIBRARIES ${${KIT}_TARGET_LIBRARIES}
  )
