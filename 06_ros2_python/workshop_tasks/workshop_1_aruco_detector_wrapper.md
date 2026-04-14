# Student 1 — ArUco Detector Wrapper

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

