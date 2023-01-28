# RT-Assignment-2

# Instruction

We were provided with an implementation of an action server that moves a robot in the environment. We were asked to implement 3 nodes aswell as update the launch file to start the whole simulation.

- A node that implements an action client, allowing the user to set a target (x, y) or to cancel it. The node also publishes the robot position and velocity as a custom message (x,y, vel_x, vel_z), by relying on the values published on the topic /odom. Please consider that, if you cannot implement everything in the same node, you can also develop two different nodes, one implementing the user interface and one implementing the publisher of the custom message.

- A service node that, when called, prints the number of goals reached and cancelled;

- A node that subscribes to the robot’s position and velocity (using the custom message) and prints the distance of the robot from the target and the robot’s average speed. Use a parameter to set how fast the node publishes the information.

# Nodes

6 nodes in total inside the script folder:

- `bug_as.py` implements the action server node.The node receives the desired position from the client and calls the useful services in oreder to bring the robot to the given position.The position is set as a ROS parameter.

- `go_to_point_service.py` implements a service node. It makes the robot move to the desired position when the node is called.

- `wall_follow_service.py`implements also a service node. It helps the robot avoiding obstacles by making it moving along/around them.
 
- `action_client.py` (node a) implements the action client node that will ask the user to enter two coordinates (x,y). Then, it will publish the position and velocity of the robot as a custom message on the /Posevelocity topic, getting the values from the `/odom` topic.
 
- `service.py` (node b) implements a service node. When the node is called,it prints how many times a desired position was reached or cancelled.

- `robot_info.py` (node c) implements a node that prints the distance between the actual position of the robot and the desired position and the average speed of the robot.These parameters are taken from the /Posevelocity topic as a custom message. The frequency of printing is set as a parameter in the launch file.

# Install and run

1. Create a workspace

2. Git clone (https://github.com/jodebelle/RT-Assignment-2)

3. catkin_make to ensure the files are executable

4. Install xterm

5. To run the program: `roslaunch assignment_2_2022 assignment1.launch`
