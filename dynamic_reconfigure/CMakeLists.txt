cmake_minimum_required(VERSION 3.8)
project(dynamic_reconfigure)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/BoolParameter.msg"
  "msg/ConfigDescription.msg"
  "msg/Config.msg"
  "msg/DoubleParameter.msg"
  "msg/Group.msg"
  "msg/GroupState.msg"
  "msg/IntParameter.msg"
  "msg/ParamDescription.msg"
  "msg/SensorLevels.msg"
  "msg/StrParameter.msg"
  DEPENDENCIES std_msgs
)

include_directories(
        ${dynamic_reconfigure_INCLUDE_DIRS}
)

ament_package()
