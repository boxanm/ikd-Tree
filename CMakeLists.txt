cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(ikd_tree_demo)

add_compile_options(-std=c++14)
set(CMAKE_CXX_FLAGS "-std=c++14 -pthread -O3")
#--------------------
# DEPENDENCY: eigen 3
#--------------------
find_path(EIGEN_INCLUDE_DIR NAMES signature_of_eigen3_matrix_library
  HINTS  ENV EIGEN3_INC_DIR
         ENV EIGEN3_DIR
  PATHS  Eigen/Core
         /usr/local/include
         /usr/include
  PATH_SUFFIXES include eigen3 eigen
  DOC "Directory containing the Eigen3 header files"
)

include_directories(
        ikd-Tree
    SYSTEM "${EIGEN_INCLUDE_DIR}"
)

add_library(ikd_tree ikd-Tree/ikd_Tree.cpp)