# AMBF Dockerfiles with Visualization

## Note:
The dockerfiles build on top of [Tiryoh/docker-ros-desktop-vnc](https://github.com/Tiryoh/docker-ros-desktop-vnc), which builds on top of [fcwu/docker-ubuntu-vnc-desktop](https://github.com/fcwu/docker-ubuntu-vnc-desktop) and thus allow graphical visualization by either using a web-browser or via VNC. More information can be found on the respective pages.


## Build Steps:
Please install Docker based on the official [instructions](https://docs.docker.com/engine/install/):
Afterward, depending upon which Ubuntu / ROS is preferred (`Ubuntu 20.04 with ROS Noetic` OR `Ubuntu 18.04 with ROS melodic`), build the image using the correct Dockerfile.

E.g.
```bash
cd docker-ambf/noetic
docker build -t collaborativerobotics/ambf-ros:noetic .
```

## How to run:
After a succesful build, a docker container can be instantiated with the following command:

```bash
docker run --name ambf_ros -p 6080:80 -p 5900:5900 -v /dev/shm:/dev/shm collaborativerobotics/ambf-ros:noetic
```

Once running, you can connect VNC to the docker container using "localhost:5900" as the address. Now you should be in a Linux desktop environment. AMBF can now be run as usual by following these [instructions](https://github.com/WPI-AIM/ambf/wiki/Launching-the-Simulator)



