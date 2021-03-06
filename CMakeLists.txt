cmake_minimum_required(VERSION 2.8.9)

project(ShapeVariationAnalyzer)


set(ShapeVariationAnalyzer_VERSION_MAJOR 1)
set(ShapeVariationAnalyzer_VERSION_MINOR 0)
set(ShapeVariationAnalyzer_VERSION_PATCH 4)


option(ShapeVariationAnalyzer_BUILD_SLICER_EXTENSION OFF)

if(ShapeVariationAnalyzer_BUILD_SLICER_EXTENSION)
	#-----------------------------------------------------------------------------
	# Extension meta-information
	set(EXTENSION_HOMEPAGE "http://slicer.org/slicerWiki/index.php/Documentation/Nightly/Extensions/ShapeVariationAnalyzer")
	set(EXTENSION_CATEGORY "Quantification")
	set(EXTENSION_CONTRIBUTORS "Priscille de Dumast (University of Michigan), Laura Pascal (University of Michigan), Nina Tubau (University of Michigan), Juan Carlos Prieto (University of North Carolina) ")
	set(EXTENSION_DESCRIPTION "ShapeVariationAnalyzer allows the classification of 3D models, according to their morphological variations. This tool is based on a deep learning neural network.")
	set(EXTENSION_ICONURL "https://www.slicer.org/w/images/3/30/ShapeVariationAnalyzer-Logo.png")
	set(EXTENSION_SCREENSHOTURLS "https://www.slicer.org/w/images/f/f0/FullView_ShapeVariationAnalyzer.png https://www.slicer.org/w/images/5/57/ShapeVariationAnalyzer-GUI.png")
	set(EXTENSION_DEPENDS ShapePopulationViewer)

	#-----------------------------------------------------------------------------
	# Extension dependencies
	find_package(Slicer REQUIRED)
	include(${Slicer_USE_FILE})

	add_subdirectory(ShapeVariationAnalyzer)
else()
	find_package(VTK REQUIRED)
	find_package(SlicerExecutionModel REQUIRED)
endif()

#-----------------------------------------------------------------------------
# Extension modules

#add_subdirectory(CLI/ComputeMeanShapes)
add_subdirectory(CLI/SurfaceFeaturesExtractor)
## NEXT_MODULE


#-----------------------------------------------------------------------------
if(ShapeVariationAnalyzer_BUILD_SLICER_EXTENSION)
	include(${Slicer_EXTENSION_CPACK})
endif()
