# ROS 2 Learning Workspace

This repository is a collection of ROS 2 packages created as part of a journey to learn the fundamental concepts of the Robot Operating System 2. Each package demonstrates a specific feature, serving as a practical, hands-on reference.

## Core Concepts Learned

This workspace covers the following key areas of ROS 2:

### 1. ROS 2 Workspace & Packages
A ROS 2 workspace is a directory containing ROS 2 packages. This workspace (`learning_ros_ws`) is a standard example.

- **Packages**: The fundamental unit of organization in ROS 2. Each subdirectory in `src/` is a package (e.g., `py_pubsub`, `learning_tf2_py`).
- **`package.xml`**: Provides meta-information about the package (name, version, dependencies).
- **`setup.py` / `CMakeLists.txt`**: Contains build information for Python and C++ packages, respectively.

### 2. ROS 2 Nodes
Nodes are the main executable programs in a ROS 2 system. They are responsible for a single, modular purpose (e.g., controlling a wheel motor, publishing sensor data).

- **Example**: `my_package/my_package/my_node.py` is a basic implementation of a ROS 2 node.

### 3. Communication Paradigms

#### a. Topics (Publish/Subscribe)
Topics provide an anonymous, asynchronous communication bus. Nodes can publish messages to a topic, and any node can subscribe to that topic to receive them.

- **Implementation**: The `py_pubsub` package demonstrates a simple publisher (`publisher_member_function.py`) and subscriber (`subscriber_member_function.py`).

#### b. Services (Client/Server)
Services are used for synchronous, request/reply communication. A client sends a request and waits for a response from a server.

- **Implementation**: The `py_srvcli` package shows how to create a service server (`service_member_function.py`) and a client (`client_member_function.py`).

#### c. Actions
Actions are used for long-running, asynchronous tasks that provide feedback. They are like services but include feedback and the ability to preempt the goal.

- **Implementation**: The `fibonacci_action_server.py` and `fibonacci_action_client.py` provide a clear example of an action.

### 4. Custom Interfaces (Messages, Services, Actions)
ROS 2 allows you to define your own data structures for communication.

- **Custom Messages (`.msg`)**: Defines the data structure for a topic.
  - **Example**: `tutorial_interfaces/msg/Num.msg`
- **Custom Services (`.srv`)**: Defines the request and response data structures for a service.
  - **Example**: `tutorial_interfaces/srv/AddThreeInts.srv`
- **Custom Actions (`.action`)**: Defines the goal, result, and feedback data structures for an action.
  - **Example**: `custom_action_interfaces/action/Fibonacci.action`

### 5. Parameters
Parameters allow you to configure a node's settings externally at startup or runtime without changing the code.

- **Implementation**: The `python_parameters` package demonstrates how to declare, set, and use parameters in a node.
- **Event Handling**: The `python_parameter_event_handler` package shows how to respond to parameter changes dynamically.

### 6. Launch Files
Launch files are used to start and configure multiple nodes at once, creating a complex system from simple parts.

- **Implementation**: The `py_launch_example` and `learning_tf2_py/launch` directories contain Python-based launch files that demonstrate how to launch nodes and set up a system like `turtlesim`.

### 7. TF2 (Transformations)
TF2 is a system that manages and keeps track of multiple coordinate frames over time. It's essential for any robot that needs to reason about the relationship between different parts (e.g., base, arm, gripper) and the world.

- **Implementation**: The `learning_tf2_py` package uses `turtlesim` to show:
  - **Broadcasting**: Publishing the relationship between coordinate frames.
  - **Listening**: Subscribing to transforms to compute the difference between frames.

### 8. Simulation and Robot Modeling
This workspace includes packages for a real robot (`Yahboom Rosmaster`), demonstrating how the core concepts are applied to hardware.

- **URDF (`.urdf`)**: The Unified Robot Description Format is an XML file used to model a robot's physical structure.
  - **Example**: `yahboom_rosmaster_description/urdf/`
- **Gazebo Simulation**: Gazebo is a powerful 3D robot simulator. The `yahboom_rosmaster_gazebo` package contains the necessary files to simulate the robot in a virtual environment.

## How to Use This Workspace

1.  **Clone the repository (if you haven't already):**
    ```bash
    git clone <your-repo-url> learning_ros_ws
    cd learning_ros_ws
    ```

2.  **Build the workspace:**
    From the root of the workspace (`learning_ros_ws`), run the `colcon` build tool.
    ```bash
    colcon build
    ```

3.  **Source the environment:**
    After a successful build, source the overlay to make the packages available in your terminal session.
    ```bash
    source install/setup.bash
    ```

4.  **Run a launch file:**
    You can now run executables or launch files from any package. For example, to run the `turtlesim` TF2 demo:
    ```bash
    ros2 launch learning_tf2_py turtle_tf2_demo_launch.py
    ```

## Packages in this Workspace

*   **`custom_action_interfaces`**: Defines a custom action for the Fibonacci sequence.
*   **`learning_tf2_py`**: Demonstrates how to use TF2 with `turtlesim` to broadcast and listen for coordinate frame transformations.
*   **`mecanum_drive_controller`**: A controller for a mecanum-drive mobile base, allowing for omnidirectional movement.
*   **`my_package`**: A basic "Hello World" ROS 2 node, serving as a minimal example of a package.
*   **`py_launch_example`**: Contains a Python-based launch file for starting ROS 2 nodes.
*   **`py_pubsub`**: Implements a simple publisher and subscriber to demonstrate topic-based communication.
*   **`py_srvcli`**: Provides a simple service and client for request/reply communication.
*   **`python_parameter_event_handler`**: Shows how to dynamically respond to parameter changes.
*   **`python_parameters`**: Demonstrates how to declare, set, and use parameters in a ROS 2 node.
*   **`turtlesim`**: A tool for teaching and learning ROS 2 concepts in a simple, visual environment.
*   **`tutorial_interfaces`**: Defines custom message and service types for inter-node communication.
*   **`yahboom_rosmaster`**: A metapackage that groups all the packages related to the Yahboom Rosmaster robot.
*   **`yahboom_rosmaster_bringup`**: Contains launch files for starting the Yahboom Rosmaster robot.
*   **`yahboom_rosmaster_description`**: Contains the URDF (robot model) and other description files for the Yahboom Rosmaster.
*   **`yahboom_rosmaster_gazebo`**: Provides the necessary files to simulate the Yahboom Rosmaster robot in the Gazebo environment.
*   **`yahboom_rosmaster_system_tests`**: Contains system-level tests for the Yahboom Rosmaster robot.

