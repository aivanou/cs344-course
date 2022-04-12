############################################################################
# <summary> CMakeLists.txt for OpenCV and CUDA. </summary>
# <date>    2012-02-07          </date>
# <author>  Quan Tran Minh. edit by Johannes Kast, Michael Sarahan </author>
# <email>   quantm@unist.ac.kr  kast.jo@googlemail.com msarahan@gmail.com</email>
############################################################################

cmake_minimum_required(VERSION 2.6 FATAL_ERROR)
project(cs344)

find_package(OpenCV REQUIRED)
find_package(CUDA REQUIRED)

enable_language(CUDA)


link_libraries(${OpenCV_LIBS} )

set (EXECUTABLE_OUTPUT_PATH "${CMAKE_SOURCE_DIR}/bin/")

if(CUDA_FOUND)
  # add debugging to CUDA NVCC flags.  For NVidia's NSight tools.
  set(CUDA_NVCC_FLAGS_DEBUG ${CUDA_NVCC_FLAGS_DEBUG} "-G")

  include_directories("${CUDA_INCLUDE_DIRS}")

  add_subdirectory (problem_set/ps1)
  #add_subdirectory (problem_set/ps2)
  #add_subdirectory (problem_set/ps3)
  #add_subdirectory (problem_set/ps4)
  #add_subdirectory (problem_set/ps5)
  #add_subdirectory (problem_set/ps6)
else(CUDA_FOUND)
  message("CUDA is not installed on this system.")
endif()
