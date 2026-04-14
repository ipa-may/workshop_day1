# Student 8 — Pen On/Off Controller

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

