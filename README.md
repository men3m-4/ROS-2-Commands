# ROS 2 Commands 

## General Format of ROS 2 CLI
- Every ROS 2 command starts with the `ros2` keyword, followed by a command, a verb, and optionally positional/optional arguments.
- **General command format**:
  ```bash
  ros2 [command] [verb] <positional-argument> <optional-arguments>
  ```
- **Help Commands**:
  ```bash
  ros2 [command] --help
  ros2 [command] [verb] -h
  ```

---

## 1. Action Commands

### Definition
An Action is a type of message-based communication that allows nodes to send goals and receive feedback on task progress.

### General Syntax
```bash
ros2 action [verb] <arguments>
```

### Verbs
- **list**: Identify all actions in the ROS graph.
- **info `<action_name>`**: Introspect about an action.
- **send_goal `<action_name>` `<action_type>` `<values>`**: Send an action goal.
  - `-f`: Show continuous feedback during execution.

### Examples
```bash
ros2 action list
ros2 action info /turtle1/rotate_absolute
ros2 action send_goal /turtle1/rotate_absolute turtlesim/action/RotateAbsolute '{theta: 1.57}'
```

---

## 2. Bag Commands

### Definition
A Bag is a file format used to record and replay ROS 2 topic data.

### General Syntax
```bash
ros2 bag [verb] <arguments>
```

### Verbs
- **record `<topic_name>`**: Record data from a topic.
- **info `<bag_file_name>`**: Get details about a bag file.
- **play `<bag_file_name>`**: Replay a recorded bag file.

### Examples
```bash
ros2 bag record /turtle1/cmd_vel
ros2 bag info my_bag.db3
ros2 bag play my_bag.db3
```

---

## 3. Component Commands

### Definition
Components are modular software units encapsulating functionality, data, and communication.

### General Syntax
```bash
ros2 component [verb] <arguments>
```

### Verbs
- **list**: List running containers and components.
- **load**: Load a component into a container node.

### Examples
```bash
ros2 component list
ros2 component load /ComponentManager composition composition::Talker
```

---

## 4. Control Commands

### Definition
A framework for integrating hardware and managing controllers.

### General Syntax
```bash
ros2 control [verb] <arguments>
```

### Verbs
- **list_controllers**: List loaded controllers and their status.

### Examples
```bash
ros2 control list controllers
```

---

## 5. Daemon Commands

### Definition
A background process providing services to ROS nodes and components.

### General Syntax
```bash
ros2 daemon [verb]
```

### Verbs
- **start**: Start the daemon if it isn’t running.

### Examples
```bash
ros2 daemon start
```

---

## 6. Doctor Commands

### Definition
Checks system health and warns about potential issues.

### Command
```bash
ros2 doctor --report
```

---

## 7. Extensions & Interfaces

### Extensions
- Lists extensions of a package.
```bash
ros2 extensions --all
```

### Interface
- List available message, service, or action types.
```bash
ros2 interface list
ros2 interface show turtlesim/msg/Pose
```

---

## 8. Launch File

### Definition
Allows launching multiple nodes with configurations in one command.

### Command
```bash
ros2 launch [package_name] [launch_file_name]
```

---

## 9. Lifecycle Management

### Definition
Manage node states using transitions (e.g., configure, activate).

### Commands
```bash
ros2 lifecycle list
ros2 lifecycle set /node_name configure
```

---

## 10. Node Management

### Running Nodes
```bash
ros2 run [package_name] [executable_name]
```

### Interacting with Nodes
```bash
ros2 node list
ros2 node info /node_name
```

---

## 11. Package Management

### Create a Package
For Python:
```bash
cd <workspace>/src && ros2 pkg create --build-type ament_python my_package_name
```

For C++:
```bash
cd <workspace>/src && ros2 pkg create --build-type ament_cmake my_package_name
```

---

## 12. Parameters Management

### List Parameters
```bash
ros2 param list /node_name
```

### Set Parameter Value
```bash
ros2 param set /node_name parameter_name value
```

---

## 13. rqt Tools

### Graphical tools for visualizing nodes and topics.
```bash
rqt graph
```

---

## 14. Security Tools (sros2)

### Manage security artifacts like keystores and permissions.
```bash
ros2 security create keystore demo_keystore
```

---

## 15. Services Management

### List Services
```bash
ros2 service list
```

### Call a Service
```bash
ros2 service call /service_name service_type '{arguments}'
```

---

## 16. Topics Management

### List Topics
```bash
ros2 topic list
```

### Publish to Topic
```bash
ros2 topic pub --once /topic_name msg_type '{data}'
```

---

## 17. Workspace Management & colcon Tools

### Create Workspace Directory
```bash
mkdir -p my_workspace/src && cd my_workspace && colcon build && source install/setup.bash
```

### Build Packages with colcon
Build all packages in the workspace or selectively build specific packages.
```bash
colcon build --packages-select my_package_name --symlink-install --parallel-workers N
```

---
