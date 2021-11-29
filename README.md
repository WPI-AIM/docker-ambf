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

Once running, you can connect VNC to the docker container using "localhost:5900" as the address (or whatever port you set above). The VNC viewer should take you inside a Linux desktop environment. AMBF can now be run as usual by following these [instructions](https://github.com/WPI-AIM/ambf/wiki/Launching-the-Simulator).

If you stop the container (purposefully or restart your machine), it can be re-run by using the "name" that we used for it earlier as follows.

```bash
docker start ambf-ros-noetic
```

To run on windows: 
1. Clone the repo 
2. Download VNC viewer: https://www.realvnc.com/en/connect/download/viewer/ 
2. Open a terminal and navigate to the repo folder (the folder with Dockerfile in it)
3. Enter the following in the terminal (you select 'name' and 'image name'): 
``` 
docker build -t 'name'
```
The first time you run it: 
```
docker run -'name' 'image_name' -p 6080:80 -p 5900:5900 -v /dev/shm:/dev/shm 'image_name'
```
4. Open VNC viewer, press File -> Start new connection and type localhost:5900 as the name
5. Press connect and you should see this: 

6. To stop the container when you're finished, open another terminal and type: 
``` 
docker stop 'name'
```
7. If you want to restart the connection 
```
docker start 'name'
```
Note: you can also make your own private docker repo to save local changes to this container: https://docs.docker.com/docker-hub/



