# AMBF Dockerfiles with Visualization

## Note:
The Docker files in this repo are built on top of [Tiryoh/docker-ros-desktop-vnc](https://github.com/Tiryoh/docker-ros-desktop-vnc) (which builds on top of [fcwu/docker-ubuntu-vnc-desktop](https://github.com/fcwu/docker-ubuntu-vnc-desktop)). The resulting Docker images allow graphical visualization by either using a web browser or [VNC](https://www.realvnc.com/en/connect/download/viewer/).


## Build Steps:
Please install Docker based on the official [instructions](https://docs.docker.com/engine/install/):
Afterward, depending upon which Ubuntu / ROS is preferred (`Ubuntu 20.04 with ROS Noetic` OR `Ubuntu 18.04 with ROS melodic`), build the image using the correct Dockerfile.

E.g.
```bash
cd docker-ambf/noetic
docker build -t collaborativerobotics/ambf-ros:noetic .
```

The build process can take a little while.

## How to run:
After succesfully building the Docker image, a Docker container can be instantiated with the following command:

```bash
docker run --name ambf-ros-noetic -p 6080:80 -p 5900:5900 -v /dev/shm:/dev/shm collaborativerobotics/ambf-ros:noetic
```

Once running, you can connect VNC to the docker container using "localhost:5900" as the address (or whatever port you set above). The VNC viewer should take you inside a Linux desktop environment (see picture below). AMBF can now be run as usual by following these [instructions](https://github.com/WPI-AIM/ambf/wiki/Launching-the-Simulator).

![image](https://user-images.githubusercontent.com/36430552/145600599-49c6bbc2-ee87-4c66-b0e1-5f938f46335a.png)

If you stop the container (purposefully or restart your machine), it can be re-run by using the "name" that we used for it earlier as follows.

```bash
docker start ambf-ros-noetic
```

To stop the container when you're finished, open another terminal and type: 
``` 
docker stop ambf-ros-noetic
```

Note: to keep changes you make in VNC desktop environment, you can also make your own private docker repo to save local changes to this container: https://docs.docker.com/docker-hub/ (see docker commit, docker push)



