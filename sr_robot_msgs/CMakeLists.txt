cmake_minimum_required(VERSION 3.10.2)
project(sr_robot_msgs)

# Default to C++17
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

# Disable Wredundant-decls warnings since rosidl generates redundant function
#  declarations
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  set(CMAKE_CXX_FLAGS
    "${CMAKE_CXX_FLAGS} -Wall -Wextra -Wpedantic -Wno-redundant-decls")
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(action_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(moveit_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

set(msg_files
"msg/ActuatorStatistics.msg"
"msg/AuxSpiData.msg"
"msg/BiotacAll.msg"
"msg/Biotac.msg"
"msg/CartesianData.msg"
"msg/CartesianPosition.msg"
"msg/Command.msg"
"msg/Config.msg"
"msg/Contrlr.msg"
"msg/ControllerStatistics.msg"
"msg/ControlType.msg"
"msg/EthercatDebug.msg"
"msg/FromMotorDataType.msg"
"msg/GraspArray.msg"
"msg/HybridControllerStatus.msg"
"msg/JointControllerState.msg"
"msg/Joint.msg"
"msg/JointMusclePositionControllerState.msg"
"msg/JointMuscleValveControllerCommand.msg"
"msg/JointMuscleValveControllerState.msg"
"msg/JointsData.msg"
"msg/JointStatistics.msg"
"msg/MechanismStatistics.msg"
"msg/MidProxDataAll.msg"
"msg/MidProxData.msg"
"msg/MotorSystemControls.msg"
"msg/MST.msg"
"msg/MSTAll.msg"
"msg/ReverseKinematics.msg"
"msg/SendUpdate.msg"
"msg/ShadowContactStateStamped.msg"
"msg/ShadowPST.msg"
"msg/TactileArray.msg"
"msg/Tactile.msg"
"msg/UBI0All.msg"
"msg/UBI0.msg"
"msg/WrenchWithModelGroupName.msg"
"msg/WrenchArray.msg"
)

set(srv_files
  "srv/ChangeControlType.srv"
  "srv/ChangeMotorSystemControls.srv"
  "srv/ForceController.srv"
  "srv/GetSegmentedLine.srv"
  "srv/IsHandOccupied.srv"
  "srv/ManualSelfTest.srv"
  "srv/NullifyDemand.srv"
  "srv/RobotTeachMode.srv"
  "srv/SetDebugData.srv"
  "srv/SetEffortControllerGains.srv"
  "srv/SetMixedPositionVelocityPidGains.srv"
  "srv/SetPidGains.srv"
  "srv/SimpleMotorFlasher.srv"
  "srv/WhichFingersAreTouching.srv"
  "srv/GetFastGraspFromBoundingBox.srv"
  "srv/PlanTrajectoryFromList.srv"
  "srv/PlanTrajectoryFromPrefix.srv"
  "srv/PlanNamedTrajectory.srv"
  "srv/ExecutePlannedTrajectory.srv"
  "srv/ListNamedTrajectories.srv"
  "srv/SetTeachMode.srv"
  "srv/SetImuScale.srv"
)

set(action_files
  "action/Grasp.action"
  "action/PlanGrasp.action"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  ${action_files}
  DEPENDENCIES
    action_msgs
    builtin_interfaces
    std_msgs
    geometry_msgs
    moveit_msgs
    sensor_msgs
)

ament_export_dependencies(rosidl_default_runtime)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
