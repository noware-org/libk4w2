
if (WITH_LIBGPUJPEG)
  link_directories(${LIBGPUJPEG_LIBRARY_DIRS})
  link_libraries (${LIBGPUJPEG_LIBRARIES})
endif()

if(WITH_OPENCV)
  include_directories(${OpenCV_INCLUDE_DIRS})
  link_directories(${OpenCV_LIBRARY_DIRS})
endif()

if(WITH_OPENCV)
  add_executable(liveview liveview.cpp)
  target_link_libraries (liveview k4w2 ${OpenCV_LIBRARIES})

  add_executable(opencv opencv.cpp)
  target_link_libraries (opencv k4w2 ${OpenCV_LIBRARIES})
endif(WITH_OPENCV)

add_executable(simple simple.c)
target_link_libraries (simple k4w2)

if (WITH_GLFW3)
add_executable(opengl opengl.c)
target_link_libraries (opengl k4w2)
target_link_libraries (opengl ${GLFW3_LIBRARIES} ${GLEW_LIBRARIES} ${OPENGL_LIBRARIES})
endif()
