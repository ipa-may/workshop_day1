# Student 3 — Action to Motor Commands

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

