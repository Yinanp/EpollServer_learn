add_definitions(-std=c++14)
cmake_minimum_required(VERSION 2.8.12)
project(nginx)

aux_source_directory(app app)
aux_source_directory(logic logic)
aux_source_directory(misc misc)
aux_source_directory(net  net)
aux_source_directory(proc proc)
aux_source_directory(signal signal)

include_directories(_include)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)

#link_directories(../static_lib_aarch/lib )

#add_executable(seism_detect include/seism.h src/main.cpp ${bo} ${dao} ${entity} ${util})
#测试使用
add_executable(nginx   ${app} ${misc} ${logic} ${net} ${proc} ${signal})
target_link_libraries(nginx pthread)
#target_link_libraries(seism_daemon pthread curl expat liblog4cxx.a libapr-1.a libaprutil-1.a liblog_c_sdk_static.a crypto)

