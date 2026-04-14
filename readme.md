# Training Material for day 1


## Installations

- ROS 2 installed : https://docs.ros.org/en/jazzy/Installation/Alternatives/Ubuntu-Install-Binary.html
    - humble for ubuntu 22.04
    - jazzy for ubuntu 24.04
- Terminator installed: https://wiki.ubuntuusers.de/Terminator/
    - `sudo apt-get install terminator`
- Git installed: https://wiki.ubuntuusers.de/Git/
    - `sudo apt install git`
- Docker for ubuntu: https://docs.docker.com/engine/install/ubuntu/
    - install using the apt repository
    - allow non-priviledge users with the post installation steps

- VS Code: https://code.visualstudio.com/docs/setup/linux#_install-vs-code-on-linux

- Bashrc:

```sh
source /opt/ros/jazzy/setup.bash
source /usr/share/colcon_argcomplete/hook

#export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
export RMW_IMPLEMENTATION=rmw_fastrtps_cpp
export ROS_DOMAIN_ID=0
```

## Exercices

1. Linux Commands

2. Git

3. CLI with turtlesim

ROS_DOMAIN_ID


## Material

https://ros2-industrial-workshop.readthedocs.io/en/latest/


## Useful links

1. https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools.html
2. ROS-I workshop: https://ros-industrial.github.io/ros2_i_training/ (corrected)

3. ROS metrics: https://metrics.ros.org/