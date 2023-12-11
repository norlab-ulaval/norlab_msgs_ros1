cmake_minimum_required(VERSION 3.8)
project(warthog_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()
set(CMAKE_BUILD_TYPE "Release")
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
	"msg/Lights.msg"
	"msg/RGB.msg"
	"msg/Status.msg"
	DEPENDENCIES std_msgs builtin_interfaces
)

install(FILES ros_bridge_mapping.yaml
	DESTINATION share/${PROJECT_NAME}
)

ament_package()
