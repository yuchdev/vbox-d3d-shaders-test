set(TARGET dynamic_shaders)

if(DirectX_D3D8_INCLUDE_FOUND)
    message("Add Direct3D 8 includes: " ${DirectX_D3D8_INCLUDE_DIR})
    include_directories(${DirectX_D3D8_INCLUDE_DIR})
endif()

if(DirectX_D3D9_INCLUDE_FOUND)
    message("Add Direct3D 9 includes: " ${DirectX_D3D9_INCLUDE_DIR})
    include_directories(${DirectX_D3D9_INCLUDE_DIR})
endif()

link_directories(${DirectX_ROOT_DIR}/Lib/x86)

file(GLOB RC *.rc ${CMAKE_CURRENT_SOURCE_DIR})
source_group("RC" FILES ${RC})

file(GLOB HLSL *.hlsl ${CMAKE_CURRENT_SOURCE_DIR})
source_group("HLSL" FILES ${HLSL})

add_executable(${TARGET} WIN32 shaders.cpp resource.h targetver.h ${RC})
target_link_libraries(${TARGET} d3d9 d3dx9)
