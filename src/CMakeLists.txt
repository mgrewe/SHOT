
#set(VTK_DIR "PATH/TO/VTK/BUILD/DIRECTORY")
FIND_PACKAGE(VTK REQUIRED)
include(${VTK_USE_FILE})

FIND_PACKAGE( OpenCV REQUIRED )

FIND_PACKAGE( OpenMP REQUIRED)
if(OPENMP_FOUND)
message("OPENMP FOUND")
	set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
	set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
endif()

ADD_EXECUTABLE(SHOT 
	${PROJECT_SOURCE_DIR}/include/randutil.h
	${PROJECT_SOURCE_DIR}/include/shot.h
	${PROJECT_SOURCE_DIR}/include/utils.h
	${PROJECT_SOURCE_DIR}/src/SHOTMain.cpp
	${PROJECT_SOURCE_DIR}/src/shot.cpp
	${PROJECT_SOURCE_DIR}/src/MeshPointsIndex.cpp
	${PROJECT_SOURCE_DIR}/src/utils.cpp
	${PROJECT_SOURCE_DIR}/src/randutil.cpp )
	
TARGET_LINK_LIBRARIES(SHOT
	${OpenCV_LIBS}
    ${VTK_LIBRARIES}
    )

