# Modified Tello_driver package with PI closed loop

(Before launching the asservissement_PI.launch, there is a need to roslaunch the tello_node.launch and be connected to the tello drone)

REQUIREMENTS##########################################################
THIS PACKAGE IMPLEMENTS A PI CLOSED LOOP AND A CAPTURE POSITION USING OPTITRACK'S CAMERAS

ROS MELODIC

THE ROS PACKAGE mocap_optitrack and the rrt_lib available on this git are REQUIRED

PLEASE REWRITE THE PATH FOR THE CSV FILES, in the asservissement_PI.cpp at section "FOR THE PLOT IN PYTHON", to be associated with the 3D-RRT-and-visualisation-for-holonomic-systems-and-DynIbex-Application repo (on this git) plot_trajectory.py

#######################################################################


IF YOU ALREADY HAVE THE TELLO_DRIVER#######################################

CHECK THE LAUNCH REPO OF THIS PACKAGE 

RECUPERATE THE RIGHT SRC FILES ASSOCIATED WITH THEM AND MODIFY YOUR Cmake and package.xml FOR THE TWO REQUIRED PACKAGES AND THE LAUNCHERS IN THE LAUNCH REPO

############################################################################

Here an example of the config file of the mocap 
/opt/ros/melodic/share/mocap_optitrack/config/mocap.yaml 

#
# Definition of all trackable objects
# Identifier corresponds to Trackable ID set in Tracking Tools
#
rigid_bodies:
    '24':                                                           //MODIFY THE ID NUMBER of your rigid body in the mocaptitrack interface
        pose: Robot_1/pose
        pose2d: Robot_1/ground_pose
        odom: Robot_1/Odom
        tf: tf
        child_frame_id: Robot_1/base_link
        parent_frame_id: world
    '25':
        pose: Cible/pose
        pose2d: Cible/ground_pose
        odom: Cible/Odom
        tf: tf
        child_frame_id: Cible/base_link
        parent_frame_id: world
optitrack_config:
        multicast_address:                                            //ADRESS OF YOUR PLACE
        command_port: 1510
        data_port: 1511
        enable_optitrack: true
