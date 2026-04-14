# Student 6 — Bool to RGB

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

