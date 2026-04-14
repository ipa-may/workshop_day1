# Student 4 — Motor Commands to Turtlesim Velocity

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

