# misa_util_msgs

Shared **misa-brand** ROS2 interface definitions. A standalone `ament_cmake`
rosidl package so any misa node can depend on the messages without pulling in
an application's implementation.

## Contents

| interface | kind | used by |
|---|---|---|
| `SwitchMode.srv` | service | `misa_bilateral` (`switch_control_mode`, `switch_servo_state`) |

```
# SwitchMode.srv
string mode
---
bool success
string message
```

## Build

Build inside a ROS2 (Jazzy) workspace with colcon. To get Rust bindings, build
within a ros2_rust overlay so `rosidl_generator_rs` runs:

```bash
# in your ROS2 workspace src/
git clone <this repo> misa_util_msgs
cd .. && colcon build --packages-select misa_util_msgs
```

Consumers (e.g. `misa_bilateral`) declare `<depend>misa_util_msgs</depend>` in
their `package.xml`.
