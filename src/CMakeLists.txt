add_subdirectory(common)
add_subdirectory(uiframe)

file(GLOB_RECURSE _SOURCES 
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/implot/*.cpp)

file(GLOB_RECURSE _HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.h
    ${CMAKE_CURRENT_SOURCE_DIR}/implot/*.h)

set(SOURCES ${_SOURCES})
set(HEADERS ${_HEADERS})

set(UIFRAME_SOURCES ${SOURCES} ${HEADERS})

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${UIFRAME_SOURCES})

add_executable(customgui main.cpp ${SOURCES} ${HEADERS})

target_include_directories(customgui PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui
    ${CMAKE_CURRENT_SOURCE_DIR}/implot
    )

set(libpath "${PROJECT_SOURCE_DIR}/lib")


target_link_libraries(customgui PUBLIC
                        ${libpath}/GLFW/glfw3.lib)

target_link_libraries(customgui PUBLIC ${OPENGL_LIBRARIES})

