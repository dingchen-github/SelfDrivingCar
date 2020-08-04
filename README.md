This is the final project of the Udacity Self-Driving Car Nanodegree: Programming a Real Self-Driving Car.

## Repo overview

This project is run in ROS. The predefined ROS architecture is shown below.

![1.png](./ROS_architecture.png)

The code is first written in this repo and then copied to Udacity Workspace for simulation.

Following ROS packages are to be implemented by me in /ros/src/:

* tl_detector: traffic light detection node. This node takes in data from the `/image_color`, `/current_pose`, and `/base_waypoints` topics and publishes the locations to stop for red traffic lights to the `/traffic_waypoint` topic.

* waypoint_updater: waypoint updater node. This node will subscribe to the `/base_waypoints`, `/current_pose`, `/obstacle_waypoint`, and `/traffic_waypoint` topics, and publish a list of waypoints ahead of the car with target velocities to the `/final_waypoints` topic.

* twist_controller: drive-by-wire (DBW) control node. This node subscribes to the `/current_velocity` topic along with the `/twist_cmd` topic to receive target linear and angular velocities. Additionally, this node will subscribe to `/vehicle/dbw_enabled`, which indicates if the car is under dbw or driver control. This node will publish throttle, brake, and steering commands to the `/vehicle/throttle_cmd`, `/vehicle/brake_cmd`, and `/vehicle/steering_cmd` topics.

Following ROS packages are predefined in /ros/src/:

* styx: A package that contains a server for communicating with the simulator, and a bridge to translate and publish simulator messages to ROS topics.

* styx_msgs: A package which includes definitions of the custom ROS message types used in the project.

* waypoint_loader: A package which loads the static waypoint data and publishes to `/base_waypoints`.

* waypoint_follower: A package containing code from Autoware which subscribes to `/final_waypoints` and publishes target vehicle linear and angular velocities in the form of twist commands to the `/twist_cmd` topic.
