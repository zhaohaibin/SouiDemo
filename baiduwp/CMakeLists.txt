﻿#
# 1394020320@qq.com
#

include_directories(${PROJECT_SOURCE_DIR}/config)
include_directories(${PROJECT_SOURCE_DIR}/components)
include_directories(${PROJECT_SOURCE_DIR}/utilities/include)
include_directories(${PROJECT_SOURCE_DIR}/SOUI/include)
include_directories(${PROJECT_SOURCE_DIR}/soui-sys-resource)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

file(GLOB_RECURSE CURRENT_HEADERS  *.h *.hpp)
file(GLOB_RECURSE CURRENT_SRCS  *.cpp)
file(GLOB_RECURSE CURRENT_SOUIS  *.xml *.idx *.ico)
file(GLOB_RECURSE CURRENT_RC *.rc *.rc2)

set(EXTENDCOTROLS
	${CMAKE_SOURCE_DIR}/controls.extend/SRadioBox2.h
	${CMAKE_SOURCE_DIR}/controls.extend/SRadioBox2.cpp
)

source_group("Header Files" FILES ${CURRENT_HEADERS})
source_group("Source Files" FILES ${CURRENT_SRCS})
source_group("SoUI Resouece" FILES ${CURRENT_SOUIS})
source_group("Resource Files" FILES ${CURRENT_RC})
source_group("Extend Cotrols" FILES ${EXTENDCOTROLS})

add_executable(baiduwb WIN32 ${CURRENT_HEADERS} ${CURRENT_SRCS} ${CURRENT_SOUIS} ${CURRENT_RC} ${EXTENDCOTROLS})

add_dependencies(baiduwb soui-sys-resource)
target_link_libraries(baiduwb utilities soui ${COM_LIBS})

set_target_properties(baiduwb PROPERTIES DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX})
set_target_properties (baiduwb PROPERTIES
    FOLDER demos
)
cotire(baiduwb)
