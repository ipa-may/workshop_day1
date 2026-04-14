# Student 5 — Food Classifier

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

