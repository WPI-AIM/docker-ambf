# This is an auto generated Dockerfile for ros:ros-base
# generated from docker_images/create_ros_image.Dockerfile.em
FROM tiryoh/ros-desktop-vnc:melodic

# Source ROS
RUN apt-get update && apt-get install -y ros-melodic-tf
RUN echo 'source /opt/ros/melodic/setup.bash' >> ~/.bashrc

# Install Git, Python pip, tf
RUN apt-get update && apt-get install -y git python-pip libasound2-dev

# Clone AMBF
RUN cd  && git clone https://github.com/WPI-AIM/ambf
RUN . /opt/ros/melodic/setup.sh && cd ~/ambf && mkdir build && cd build && cmake .. && make
RUN echo 'source ~/ambf/build/devel/setup.bash' >> ~/.bashrc
