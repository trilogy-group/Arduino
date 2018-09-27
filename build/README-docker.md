# Building Arduino with Docker

[Building Arduino](https://github.com/arduino/Arduino/wiki/Building-Arduino) requires some specific dependencies versions and this task can be hard if you can't have those dependencies. For this we have created this Docker image that will allow you to build your very own version of Arduino and run it on your local machine.

## Building the Docker image

`docker build -f build/Dockerfile -t arduino .` this will build the build docker image.

## Running the image

`docker run -it --rm -v "$(pwd)":/data arduino` this command runs the docker image built on previous step and shares the current project folder to `/data` directory inside docker image and will connect you to inside the docker image.

### Running Arduino UI (linux only)

`docker run -it --rm -v "$(pwd)":/data -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --net=host arduino` this command runs the docker image built on previous step and shares host X11 with docker image so it can start Arduino UI

## Building inside Docker image

`cd build && ant run` this command will build and start Arduino

## Exporting built runnable


