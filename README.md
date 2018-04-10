# forklift_sim

# Instalation instructions

```
mkdir -p forklift_sim_ws/src
cd forklift_sim_ws/src
git clone https://github.com/wmlynar/forklift_sim.git
git clone https://github.com/carlosjoserg/rrbot
git clone https://github.com/ghliu/pyReedsShepp
cd pyReedsShepp
sudo python setup.py install
cd ..
sudo pip install shapely
#sudo apt-get install libompl-dev
sudo apt-get install ros-kinetic-gazebo-ros-pkgs ros-kinetic-gazebo-ros-control ros-kinetic-ros-controllers
catkin_make
source devel/setup.bash
```

# Running instructions

```
roslaunch forklift_gazebo forklift_world.launch
roslaunch forklift_description forklift_rviz.launch
roslaunch forklift_control action_servers.launch
rosrun forklift_planner forkliftNode.py
```

# Giving commands

Manual control

```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py cmd_vel:=/forklift/front_wheel_controller/cmd_vel
```

Planning

```
rostopic pub /forklift/planner/goal std_msgs/String "data: 'Holding forklift pallet1'"
rostopic pub /forklift/planner/goal std_msgs/String "data: 'Holding forklift None'"
rostopic pub /forklift/planner/goal std_msgs/String "data: 'On pallet1 S3'"
```
