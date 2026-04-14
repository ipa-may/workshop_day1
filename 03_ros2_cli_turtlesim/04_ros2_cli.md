# ROS 2 CLI

## About Nodes

```sh
ros2 node list
ros2 node info <node-name>
```

## Introspecting topics

```sh
ros2 topic list
ros2 topic echo <topic-name>
ros2 topic hz <topic-name> # gives the average rate in Herz
ros2 topic bw <topic-name> # average bandwidth in Byte/sec
```

## Publishing CLI

```sh
ros2 topic pub -r 5 <topic-name> <datatype> "{data: <data>}"
ros2 topic pub -r 5 /test_float32_topic example_interfaces/msg/Float32 "{data: 42.2}" # Publish Float32 5x a second
ros2 topic pub -r 10 /test_string_topic example_interfaces/msg/String "{data: 'Hello'}" # Publish String 10x a second
ros2 topic pub -r 2 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 1.0}, angular: {z: 1.0}}" # all other values are 0
```

## Service CLI

### Service request

```sh
ros2 service call /add_two_ints example_interfaces/srv/AddTwoInts "{a: 3, b: 7}"
```

### Get the interface of the service

```sh
ros2 service list
ros2 service type <service-name>
```

You can then use `ros2 interface show`

## Action CLI

### List and inspect actions

```sh
ros2 action list
ros2 action list -t # list actions with action type
ros2 action info <action-name>
ros2 action type <action-name>
```

### Send an action goal

```sh
ros2 action send_goal <action-name> <action-type> "{<goal-data>}"
ros2 action send_goal /fibonacci example_interfaces/action/Fibonacci "{order: 10}" --feedback
```

`--feedback` prints action feedback while the goal is running.

### Show action interface

```sh
ros2 interface show <action-type>
ros2 interface show example_interfaces/action/Fibonacci
```

## Inteface show

```sh
ros2 interface show <datatype>
```

## Remapping using --ros-args

It is not possible to run multiple nodes with the same name.

```sh
ros2 run <pkg-name> <exec-name> --ros-args -r __node:=<new-name> # rename a node at runtime
ros2 run <pkg-name> <exec-name> --ros-args -r <old-topic-name>:=<new-topic-name>  # remap atopic
```

**-r** for remap.

### parameters (todo)

## colcon build

Build in the workspace (outside of the src/).

```sh
colcon build --packages-select <pkg-name>
colcon build --symlink-install
```

**symlink-install** will run directly the file written and not the one inside the install/ folder. Allows to modify the file and run it without having to rebuild. Only for the development phase!

## rqt and rqt_graph

```sh
rqt
```

Useful Plugins:

- Introspection -> Node Graph (also rqt_graph)

```sh
rqt_graph
```

## ROS 2 Datatypes

### Example datatype

```sh
ros2 interface show example_interface/msg/
ros2 interface show example_interfaces/srv/
```

Comment on ros 2 version update: std::msgs is depreciated. Use example_interfaces::msg instead

```sh
ros2 interface show std_msgs/msg/String
# This was originally provided as an example message.
# It is deprecated as of Foxy
# It is recommended to create your own semantically meaningful message.
# However if you would like to continue using this please use the equivalent in example_msgs.
```

```sh
ros2 interface show example_interfaces/msg/String 
# This is an example message of using a primitive datatype, string.
# If you want to test with this that's fine, but if you are deploying
# it into a system you should create a semantically meaningful message type.
# If you want to embed it in another message, use the primitive data type instead.
string data
```
