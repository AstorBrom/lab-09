cmake_minimum_required(VERSION 3.4)

project(solve_app)

add_executable(gg equation.cpp)

target_include_directories(gg PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib
                                                   ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib   
                                                   ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib
                                                   ${CMAKE_CURRENT_SOURCE_DIR}/../solver_application)
						   
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib lol)						   
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex)                                                
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib solver)

target_link_libraries(gg lib1 lib2 lib3)
if(make_bin)
	install(TARGETS gg RUNTIME DESTINATION bin)
	set(CPACK_GENERATOR "DEB")
	set(CPACK_DEBIAN_PACKAGE_MAINTAINER "David Doria")
	set(CPACK_DEBIAN_FILE_NAME "solvering.deb")
	set(CPACK_GENERATOR "DragNDrop")
	set(CPACK_PACKAGE_FILE_NAME "solvering_dmg")
	set(CPACK_GENERATOR "RPM")
	set(CPACK_RPM_FILE_NAME solvering.rpm)
	set(CPACK_GENERATOR "WIX")
	set(CPACK_PACKAGE_FILE_NAME "wixxx")
else()
	install(FILES equation.cpp DESTINATION src)
	install(TARGETS lib1 DESTINATION src)
	install(TARGETS lib2 DESTINATION src)
	install(TARGETS lib3 DESTINATION src)
	set(CPACK_GENERATOR "TGZ")
	set(CPACK_PACKAGE_FILE_NAME "just_code")
endif()
include(CPack)
