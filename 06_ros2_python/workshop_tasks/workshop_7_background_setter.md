# Student 7 — Background Setter

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

