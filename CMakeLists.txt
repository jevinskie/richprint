cmake_minimum_required( VERSION 3.10 )
project( RichPrint )
# set( CMAKE_BUILD_TYPE Release )
# string(REPLACE "/MD" "/MT" CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE}"  )
# message(STATUS "${CMAKE_CXX_FLAGS_RELEASE} " CMAKE_CXX_FLAGS_RELEASE)
set(BUILD_SHARED_LIBS OFF)
set(CMAKE_CXX_STANDARD 17)

find_package(Boost CONFIG REQUIRED headers)
set_target_properties(Boost::headers PROPERTIES IMPORTED_GLOBAL ON)

add_executable( richprint richprint.cpp )
target_link_libraries(richprint PUBLIC Boost::headers)
target_compile_definitions(richprint PRIVATE BOOST_DLL_USE_STD_FS)

install(TARGETS richprint DESTINATION bin)
install(FILES comp_id.txt DESTINATION bin)

INCLUDE(CPack)
