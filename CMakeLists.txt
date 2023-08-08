project(umc)
cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(metal-cmake)
add_subdirectory(src)

#you need set env PATH of usd installed directory
file(GLOB RESOURCE_FILES ${CMAKE_CURRENT_SOURCE_DIR}/shaders/*.metal)
file(COPY ${RESOURCE_FILES} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
#set(USD_INSTALL_ROOT "/opt/local/OpenUSD/buidl-release")
include($ENV{USD_INSTALL_ROOT}/pxrConfig.cmake)

find_package(MaterialX REQUIRED)


add_executable(umc main.cpp)

target_link_libraries(umc PRIVATE
                        CORE
                        METAL_CPP
                        ${PXR_LIBRARIES})   
#add_executable(umc
#                main.cpp
#                appdel.cpp
#                renderer.cpp
#                view.cpp)
                
#target_link_libraries(umc PUBLIC
#                        ${PXR_LIBRARIES}
#                        METAL_CPP)   
