cmake_minimum_required(VERSION 2.7)
project(QR_SLAM)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -lzbar")
find_package( OpenCV REQUIRED )
find_package( Pangolin REQUIRED)

include_directories(
        ${PROJECT_SOURCE_DIR}
        ${PROJECT_SOURCE_DIR}/include
        ${EIGEN3_INCLUDE_DIR}
        ${Pangolin_INCLUDE_DIRS}
        /home/castoryan/zbar-0.10/include
)



set(SOURCE_FILES
        src/main.cpp
        src/System.cpp
        src/Mapper.cpp
        src/Viewer.cpp
        src/Loopper.cpp
        src/Frame.cpp
        src/KeyFrame.cpp
        src/Tracker.cpp
        src/MapPoint.cpp
        src/Initializer.cpp
        src/Map.cpp
        src/PnPsolver.cpp
        src/Optimizer.cpp include/Optimizer.h)
add_executable(QR_SLAM ${SOURCE_FILES})
target_link_libraries( QR_SLAM ${OpenCV_LIBS}
        g2o_core g2o_types_slam3d  g2o_stuff g2o_types_sba g2o_solver_dense g2o_types_data
        -lzbar ${Pangolin_LIBRARIES} )