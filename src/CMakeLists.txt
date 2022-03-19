add_subdirectory(common)
add_subdirectory(imgui)
add_subdirectory(uiframe)

file(GLOB_RECURSE _SOURCES 
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.cpp)

file(GLOB_RECURSE _HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.h)

set(SOURCES ${_SOURCES})
set(HEADERS ${_HEADERS})

add_executable(customgui main.cpp ${SOURCES} ${HEADERS})

target_include_directories(customgui PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui
    )

set(libpath "${PROJECT_SOURCE_DIR}/lib")
message("Src List: ${libpath}/GLFW/glfw3.lib")

target_link_libraries(customgui PUBLIC
                        ${libpath}/GLFW/glfw3.lib)

target_link_libraries(customgui PUBLIC ${OPENGL_LIBRARIES})

#  target_link_libraries(customgui PUBLIC
#     ${CMAKE_CURRENT_SOURCE_DIR}/../lib/opengl/glut.lib
#     ${CMAKE_CURRENT_SOURCE_DIR}/../lib/opengl/glut32.lib)

message("libpath:  ${libpath}/opengl/glut.dll")

#add_custom_command(
#    TARGET customgui POST_BUILD
#    COMMAND  ${CMAKE_COMMAND} -E copy_if_different
#    ${libpath}/opengl/glut.dll
#    ${libpath}/opengl/glut32.dll
#    $<TARGET_FILE_DIR:customgui>)
