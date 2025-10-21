# ROS2

## 1. `ros2`: Command not fount
Common error when running any `ros2` commands.

### Solution - Sourcing `setup.bash`
1. **Command way**: Run `echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc` ro automaticlly source when open terminal.
2. **Preffered way**: Go to your `.bashrc` file and manuallyy add `source /opt/ros/jazzy/setup.bash` in VS Code

## 2. Running Executables (here I am using humble version not jezzy)
```
sudo apt update
sudo apt install ros-hunble-tutlesim
```
See list of packages
```
ros2 pkg list
```
See list of <packages, executables>
```
ros2 pkg executables
```
See list of executables from turtlesim package
```
ros2 pkg executables turtlesim
```
Where is turtlesim?
```
cd /opt/ros/humble/
code .
Ctrl+P, turtlesim
```
Should see `turtlesim` is located in
```
share/ament_index/resource_index/packages
```
Run turtlesim. Do `ros2 run -h` to see options

```
ros2 run <package_name> <executable_name>
ros2 run turtlesim turtlesim_node
```
In other terminal, run the teleop mode
```
ros2 run turtlesim turtle_teleop
```

## 3. ROS2 Node Commands
1. See ros2 node help
```
ros2 node -h
```
2. List current nodes running. Right now there should be nothing
```
ros2 node list
```
3. Run a node from previous section
```
ros2 run turtlesim turtlesim_node
```
4. Now list the nodes again as **`2`** step, you should see `/turtlesim`
5. See node info
```
ros2 node info <node_name>
ros2 node info /turtlesim
```

## 4. ROS Topics
### A topic is one way data is moved between nodes. Where 1 on more publisher nodes can connect to 1 or more subscriber nodes.
1. Open new terminal and run
```
ros2 run <package_name> <executable>
ros2 run turtlesim turtlesim_node
```
2. Open new terminal and run. 
> Try to move the turtle anywhere?! (hahaha... You need to run `teleop` first)
```
ros2 run turtlesim turtle_teleop_key
```
3. See list of topics
```
ros2 topic list
# See detailes
ros2 topic list -t
```
4. Start rqt graph
```
rqt_graph
```
5. See topic output.
> Move with teleop to see output after running command
```
ros2 topic echo <topic_name>
ros2 topic echo /turtle1/cmd_vel
```
6. See topic ino
```
ros2 topic info <topic_name>
ros2 topic info /turtle1/cmd_vel
```
7. See interface definition
```
ros interface show <type>
ros interface show geometery_msgs/msg/Twist
```
8. Publish data to a toopic
> `--once` means publish once and exit
```
ros2 topic pub <topic_name> <msg_type> '<args>'
ros2 topic pub --once /turtle1/cmd_vel geometery_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"
```
9. Publish data to a topic with rate 1hz
```
ros2 topic pub --rate 1 /turtle1/cmd_vel geometery_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"
```
10. Echo the pose topic.
> Go to rqt graph and refresh
```
ros2 topic echo /turtle1/pose
```
11. View topic freq
```
ros2 opic hz <topic_name>
ros2 opic hz /turtle1/pose
```








