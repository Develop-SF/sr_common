cmake_minimum_required(VERSION 3.10.2)
project(sr_description)

find_package(ament_cmake REQUIRED)

ament_package()

# if (BUILD_TESTING)
#   find_package(urdf REQUIRED)
#   find_package(ament_cmake_gtest REQUIRED)
#   include_directories(${urdf_INCLUDE_DIRS})
#   ament_add_gtest(test_sr_description_urdf test/test_sr_description_urdf.cpp)
#   target_link_libraries(test_sr_description_urdf ${urdf_LIBRARIES})
# endif()

install(DIRECTORY hand/
   DESTINATION share/${PROJECT_NAME}/hand)

install(DIRECTORY meshes/
   DESTINATION share/${PROJECT_NAME}/meshes)

install(DIRECTORY loaders/
   DESTINATION share/${PROJECT_NAME}/loaders)

install(DIRECTORY robots/
   DESTINATION share/${PROJECT_NAME}/robots)

install(DIRECTORY other/
   DESTINATION share/${PROJECT_NAME}/other)
