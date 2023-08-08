cmake_minimum_required(VERSION 3.10)
include($ENV{USD_INSTALL_ROOT}/pxrConfig.cmake)

add_library(CORE appdel.cpp renderer.cpp view.cpp)
target_link_libraries(CORE 
                        METAL_CPP 
                        ${PXR_LIBRARIES})