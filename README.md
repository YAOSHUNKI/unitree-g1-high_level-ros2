# unitree-g1 high_level ros2
Implementing ROS2 for the high-level control of the Unitree G1. The primary focus is on walking. \
Set up the environment based on the official unitree_ros2 package from unitree.

##  reference
・https://github.com/unitreerobotics/unitree_ros2 \
・https://github.com/KobeKosenRobotics/rosenv_for_unitree

# Set up
For information on the environment, please refer to the following repository. \
https://github.com/KobeKosenRobotics/rosenv_for_unitree#reference 

# Setting Up a ROS 2 Environment
## 1.git clone src file
Please git clone the src files into the g1 directory of the unitree_ros2 examples. \
unitree_ros2/example/src/src/g1/high_level
```bash
git clone https://github.com/YAOSHUNKI/unitree-g1-high_level-ros2/src/g1_high_level_ros2.cpp
```
## 2.Changes to the include file
### Change to base_clinet.hpp
Modify `base_client.hpp` located in `unitree_ros2/example/include/common` to change the topic reception interval.
```bash
#47   auto status = response_future.wait_for(std::chrono::seconds(5));
```
Change the script on line 47 as follows
```bash
#47   auto status = response_future.wait_for(std::chrono::seconds(0));
```
### Change to g1_loco_client.hpp
Modify `g1_loco_client.hpp` in `unitree_ros2/example/include/g1` to change the runtime.
```bash
#215     return SetVelocity(vx, vy, vyaw, continous_move ? 864000.F : 1.F);
```
Change the script on line 215 as follows
```bash
#215     return SetVelocity(vx, vy, vyaw, 0.3F);
```
Here, you can set how many seconds of operation each /cmd_vel command performs. Please adjust the duration as needed.
