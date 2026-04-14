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