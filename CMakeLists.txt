cmake_minimum_required(VERSION 3.16.3...3.19.7 FATAL_ERROR)
cmake_policy(SET CMP0057 NEW)
message(STATUS "CMP0057 set to NEW")

project(AnomalousFiltersExtension)

#-----------------------------------------------------------------------------
# Extension meta-information
set(EXTENSION_HOMEPAGE "https://anomalousfiltersextension.readthedocs.io/en/latest/")
set(EXTENSION_CATEGORY "Filtering")
set(EXTENSION_CONTRIBUTORS "Antonio Carlos Senra Filho (University of Sao Paulo), Luiz Otavio Murta Junior (University of Sao Paulo)")
set(EXTENSION_DESCRIPTION "This extension aims to provide several approaches in order to apply the anomalous spatial filters on medical images. The methods provided here are numerical solution of the generalized anomalous diffusion proposed by Constantino Tsallis, which, in other words, provide a numerical solution to the porous media equation (Fokker-Planck anomalous heat equation). At the moment, the Modules available are suppose to be used on MRI volumes namely T1, T2, T2-FLAIR and PD weighted images, and diffusion weighted images (DWI and DTI). Future developments will add new functionalities in order to attenuate image noise in other imaging modalities. More details could be found in the wiki page.")
set(EXTENSION_ICONURL "https://raw.githubusercontent.com/CSIM-Toolkits/AnomalousFiltersExtension/refs/heads/main/AnomalousFiltersExtension.png")
set(EXTENSION_SCREENSHOTURLS "
https://raw.githubusercontent.com/CSIM-Toolkits/AnomalousFiltersExtension/refs/heads/main/docs/assets/MRI_raw.png 
https://raw.githubusercontent.com/CSIM-Toolkits/AnomalousFiltersExtension/refs/heads/main/docs/assets/MRI_AAD.png
https://raw.githubusercontent.com/CSIM-Toolkits/AnomalousFiltersExtension/refs/heads/main/docs/assets/MRI_IAD.png 
https://raw.githubusercontent.com/CSIM-Toolkits/AnomalousFiltersExtension/refs/heads/main/docs/assets/DTI_FA_raw.png 
https://raw.githubusercontent.com/CSIM-Toolkits/AnomalousFiltersExtension/refs/heads/main/docs/assets/DTI_FA_AAD.png
")

#-----------------------------------------------------------------------------
# Extension dependencies
find_package(Slicer REQUIRED)
include(${Slicer_USE_FILE})

#-----------------------------------------------------------------------------
# Extension modules
add_subdirectory(AADImageFilter)
add_subdirectory(IADImageFilter)
add_subdirectory(AADDiffusionWeightedData)
add_subdirectory(AADEPIData)
## NEXT_MODULE

#-----------------------------------------------------------------------------
include(${Slicer_EXTENSION_GENERATE_CONFIG})
include(${Slicer_EXTENSION_CPACK})
