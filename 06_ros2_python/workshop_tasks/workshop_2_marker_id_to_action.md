# Student 2 — Marker ID to Action

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

