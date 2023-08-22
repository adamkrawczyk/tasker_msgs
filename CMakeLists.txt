cmake_minimum_required(VERSION 3.8)
project(tasker_msgs)

# Find required packages
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# Add message and service files
set(msg_files
  "msg/TaskState.msg"
  "msg/ScheduleParams.msg"
  "msg/Status.msg"
  "msg/RobotResource.msg"
  "msg/ShdlData.msg"
  "msg/ShdlDataStamped.msg"
  "msg/CMD.msg"
)

set(srv_files
  "srv/TaskRequest.srv"
  "srv/LaunchConditions.srv"
  "srv/StartTask.srv"
  "srv/HoldConditions.srv"
  "srv/SchedulingConditions.srv"
  "srv/SuspendConditions.srv"
  "srv/CostConditions.srv"
)

# Generate messages and services
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES std_msgs geometry_msgs
)

# Create an ament index resource which references the libraries in the binary dir
ament_export_dependencies(rosidl_default_runtime)

ament_package()