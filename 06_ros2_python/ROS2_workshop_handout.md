# ROS 2 Student Handout — 8 Independent Assignments

## Mini-Project Overview

You will work in pairs? No — in this activity, **8 students each complete 1 node**.

The project is split into **2 pipelines**:

- **Pipeline A:** ArUco marker → motion commands → turtlesim movement
- **Pipeline B:** food name → fruit/vegetable logic → turtlesim appearance

Each student writes **one ROS 2 Python node**.

Use:
- **Python**
- **ROS 2**
- only **common interface messages**
- simple logic
- clean topic names

---

# Quick Reference

## Messages
- `sensor_msgs/msg/Image`
- `std_msgs/msg/Int32`
- `std_msgs/msg/String`
- `std_msgs/msg/Float64`
- `std_msgs/msg/Bool`
- `std_msgs/msg/UInt8`
- `geometry_msgs/msg/Twist`

## Services
- `std_srvs/srv/Empty`
- `turtlesim/srv/SetPen`

---

# Pipeline A

```text
/camera/color/image_raw
    ↓
[Student 1] /aruco_id
    ↓
[Student 2] /motion_action
    ↓
[Student 3] /left_motor_cmd + /right_motor_cmd
    ↓
[Student 4] /turtle1/cmd_vel
```

## Student 1 — ArUco Detector Wrapper

### Goal
Subscribe to the camera image and publish the detected ArUco marker ID.

### Subscribe
- `/camera/color/image_raw`
- Type: `sensor_msgs/msg/Image`

### Publish
- `/aruco_id`
- Type: `std_msgs/msg/Int32`

### Notes
- The instructor provides the ArUco helper logic.
- Your job is to connect it to ROS 2.

### Expected behavior
If marker `3` is detected, publish:
- `/aruco_id = 3`

---

## Student 2 — Marker ID to Action

### Goal
Convert the marker ID into an action string.

### Subscribe
- `/aruco_id`
- Type: `std_msgs/msg/Int32`

### Publish
- `/motion_action`
- Type: `std_msgs/msg/String`

### Mapping
- `0` → `STOP`
- `1` → `GO FORWARD`
- `2` → `GO BACKWARD`
- `3` → `TURN LEFT`
- `4` → `TURN RIGHT`
- anything else → `STOP`

### Example
If `/aruco_id = 1`, publish:
- `/motion_action = "GO FORWARD"`

---

## Student 3 — Action to Motor Commands

### Goal
Convert the action string into left and right motor commands.

### Subscribe
- `/motion_action`
- Type: `std_msgs/msg/String`

### Publish
- `/left_motor_cmd`
- Type: `std_msgs/msg/Float64`
- `/right_motor_cmd`
- Type: `std_msgs/msg/Float64`

### Suggested mapping
- `STOP` → left `0.0`, right `0.0`
- `GO FORWARD` → left `2.0`, right `2.0`
- `GO BACKWARD` → left `-2.0`, right `-2.0`
- `TURN LEFT` → left `-1.0`, right `1.0`
- `TURN RIGHT` → left `1.0`, right `-1.0`

### Example
If `/motion_action = "TURN LEFT"`, publish:
- `/left_motor_cmd = -1.0`
- `/right_motor_cmd = 1.0`

---

## Student 4 — Motor Commands to Turtlesim Velocity

### Goal
Subscribe to the left and right motor commands and drive the turtle.

### Subscribe
- `/left_motor_cmd`
- Type: `std_msgs/msg/Float64`
- `/right_motor_cmd`
- Type: `std_msgs/msg/Float64`

### Publish
- `/turtle1/cmd_vel`
- Type: `geometry_msgs/msg/Twist`

### Suggested conversion
- `linear.x = (left + right) / 2`
- `angular.z = (right - left) / 2`

### Example
If:
- left = `2.0`
- right = `2.0`

Then:
- `linear.x = 2.0`
- `angular.z = 0.0`

---

# Pipeline B

```text
/food_name
    ↓
[Student 5] /is_fruit
    ├──→ [Student 6] /bg_r /bg_g /bg_b
    │              ↓
    │         [Student 7] turtlesim background
    │
    └──→ [Student 8] turtlesim pen on/off
```

## Student 5 — Food Classifier

### Goal
Decide whether a given word is a fruit or a vegetable.

### Subscribe
- `/food_name`
- Type: `std_msgs/msg/String`

### Publish
- `/is_fruit`
- Type: `std_msgs/msg/Bool`

### Rule
- `True` = fruit
- `False` = vegetable

### Suggested words

Fruit:
- `apple`
- `banana`
- `pear`
- `orange`

Vegetable:
- `carrot`
- `cucumber`
- `potato`
- `tomato`

### Example
If `/food_name = "apple"`, publish:
- `/is_fruit = True`

If `/food_name = "carrot"`, publish:
- `/is_fruit = False`

---

## Student 6 — Bool to RGB

### Goal
Convert the boolean classification into RGB values for the turtlesim background.

### Subscribe
- `/is_fruit`
- Type: `std_msgs/msg/Bool`

### Publish
- `/bg_r`
- Type: `std_msgs/msg/UInt8`
- `/bg_g`
- Type: `std_msgs/msg/UInt8`
- `/bg_b`
- Type: `std_msgs/msg/UInt8`

### Mapping
- `True` (fruit) → blue
  - `r = 0`
  - `g = 0`
  - `b = 255`
- `False` (vegetable) → green
  - `r = 0`
  - `g = 255`
  - `b = 0`

### Example
If `/is_fruit = False`, publish:
- `/bg_r = 0`
- `/bg_g = 255`
- `/bg_b = 0`

---

## Student 7 — Background Setter

### Goal
Subscribe to RGB values and apply them to the turtlesim background.

### Subscribe
- `/bg_r`
- Type: `std_msgs/msg/UInt8`
- `/bg_g`
- Type: `std_msgs/msg/UInt8`
- `/bg_b`
- Type: `std_msgs/msg/UInt8`

### Use
- turtlesim parameters:
  - `background_r`
  - `background_g`
  - `background_b`
- service:
  - `/clear`
  - Type: `std_srvs/srv/Empty`

### What your node should do
1. store the latest R, G, and B values
2. update the turtlesim background parameters
3. call `/clear` so the new background is visible

### Example
If you receive:
- `r = 0`
- `g = 0`
- `b = 255`

Then the turtlesim background should become **blue**.

---

## Student 8 — Pen On/Off Controller

### Goal
Turn the turtlesim pen on or off depending on the fruit/vegetable boolean.

### Subscribe
- `/is_fruit`
- Type: `std_msgs/msg/Bool`

### Use
- `/turtle1/set_pen`
- Type: `turtlesim/srv/SetPen`

### Mapping
- `True` (fruit) → pen ON
- `False` (vegetable) → pen OFF

### Service details
- pen ON → `off = 0`
- pen OFF → `off = 1`

### Suggested pen settings
When ON:
- `r = 255`
- `g = 0`
- `b = 0`
- `width = 3`
- `off = 0`

When OFF:
- keep the same color values
- set `off = 1`

---

# Testing Examples

## Test Pipeline A
Show different ArUco markers to the camera.

### Example
Marker `1`:
- Student 1 publishes `1`
- Student 2 publishes `"GO FORWARD"`
- Student 3 publishes `2.0` and `2.0`
- Student 4 moves the turtle forward

Marker `3`:
- Student 2 publishes `"TURN LEFT"`
- Student 4 makes the turtle turn left

---

## Test Pipeline B
Publish words on `/food_name`.

### Example CLI
```bash
ros2 topic pub /food_name std_msgs/msg/String "{data: apple}" --once
```

### Expected result
- Student 5 publishes `True`
- Student 6 publishes `(0, 0, 255)`
- Student 7 sets blue background
- Student 8 turns pen ON

### Another example
```bash
ros2 topic pub /food_name std_msgs/msg/String "{data: carrot}" --once
```

### Expected result
- Student 5 publishes `False`
- Student 6 publishes `(0, 255, 0)`
- Student 7 sets green background
- Student 8 turns pen OFF

---

# Suggested Minimal Python Template

```python
import rclpy
from rclpy.node import Node

class MyNode(Node):
    def __init__(self):
        super().__init__('my_node')

def main(args=None):
    rclpy.init(args=args)
    node = MyNode()
    rclpy.spin(node)
    node.destroy_node()
    rclpy.shutdown()

if __name__ == '__main__':
    main()
```

---

# Deliverable

Each student should submit:
- one Python node
- correct topic names
- correct message/service types
- working logic for their assignment

---

# Final Reminder

Keep it simple:
- one node per student
- one clear responsibility
- correct ROS 2 communication
- test live at the end
