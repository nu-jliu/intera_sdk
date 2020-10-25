cmake_minimum_required(VERSION 2.8.3)
project(intera_interface)

find_package(catkin
  REQUIRED
  COMPONENTS
  cv_bridge
  rospy
  actionlib
  sensor_msgs
  std_msgs
  control_msgs
  trajectory_msgs
  dynamic_reconfigure
  intera_core_msgs
  intera_motion_msgs
)

catkin_python_setup()

generate_dynamic_reconfigure_options(
  cfg/SawyerPositionJointTrajectoryActionServer.cfg
  cfg/SawyerVelocityJointTrajectoryActionServer.cfg
  cfg/SawyerPositionFFJointTrajectoryActionServer.cfg
)

add_dependencies(${PROJECT_NAME}_gencfg intera_core_msgs_generate_messages_py)

catkin_package(
  CATKIN_DEPENDS
  cv_bridge
  rospy
  actionlib
  sensor_msgs
  std_msgs
  control_msgs
  trajectory_msgs
  dynamic_reconfigure
  intera_core_msgs
  intera_motion_msgs
)

catkin_install_python(
  PROGRAMS scripts/calibrate_arm.py scripts/home_joints.py
  scripts/joint_trajectory_action_server.py scripts/enable_robot.py scripts/io_config_editor.py scripts/send_urdf_fragment.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
