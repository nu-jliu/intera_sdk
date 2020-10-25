cmake_minimum_required(VERSION 2.8.3)
project(intera_examples)

find_package(catkin
  REQUIRED
  COMPONENTS
  rospy
  actionlib
  sensor_msgs
  control_msgs
  trajectory_msgs
  cv_bridge
  dynamic_reconfigure
  intera_core_msgs
  intera_motion_msgs
  intera_interface
)

catkin_python_setup()

generate_dynamic_reconfigure_options(
  cfg/SawyerJointSpringsExample.cfg
)

catkin_package(
  CATKIN_DEPENDS
  rospy
  actionlib
  sensor_msgs
  control_msgs
  trajectory_msgs
  cv_bridge
  dynamic_reconfigure
  intera_core_msgs
  intera_motion_msgs
  intera_interface
)

catkin_install_python(PROGRAMS
scripts/camera_display.py         scripts/joint_position_keyboard.py
scripts/constrained_zeroG.py      scripts/joint_position_waypoints.py
scripts/fk_service_client.py      scripts/joint_recorder.py
scripts/go_to_cartesian_pose.py   scripts/joint_torque_springs.py
scripts/go_to_joint_angles_in_contact.py scripts/joint_trajectory_client.py
scripts/go_to_joint_angles.py     scripts/joint_trajectory_file_playback.py
scripts/gripper_cuff_control.py   scripts/joint_velocity_wobbler.py
scripts/gripper_joystick.py       scripts/lights_blink.py
scripts/gripper_keyboard.py       scripts/navigator_io.py
scripts/head_display_image.py     scripts/send_random_trajectory.py
scripts/head_wobbler.py           scripts/send_traj_from_file.py
scripts/ik_service_client.py      scripts/set_interaction_options.py
scripts/joint_position_file_playback.py scripts/stop_motion_trajectory.py
scripts/joint_position_joystick.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(
  DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
  USE_SOURCE_PERMISSIONS
)

install(
  DIRECTORY share/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/share
  USE_SOURCE_PERMISSIONS
)
