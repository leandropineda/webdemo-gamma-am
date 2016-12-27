# Virtual environment for gamma-AM #

## Description ##
This is a Docker image with R 3.1.x. The R version is the one included in the CRAN repositories for Ubuntu 14.04. In addition, it contains several R packages installed (you can get more details by inspecting the [Dockerfile](https://github.com/leandropineda/webdemo-gamma-am/blob/master/Dockerfile)).

## Web demo builder ##
This Docker image can be used by the Web demo builder as a R 3.1 virtual environment. You don't need to download it or use it directly from here, just use the Web demo builder interface, select the R programming language, and specify this virtual environment: lpineda/webdemo-gamma-am

## Showing figures and plots ##
If you want to use this image as your virtual environment for your R 3.1 code (without using the Web demo builder), you might want to be able to show figures and plots within it. For this, you need to run your container with some special parameters. These parameters allows the R process inside to get access to your X11 session.

    #!bash
    sudo docker run -ti -e DISPLAY=$DISPLAY -e uid=$UID \
      -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
      lpineda/webdemo-gamma-am

Once inside the container, you will see a shell prompt like this:

    #!bash
    developer@CONTAINER_ID:/$

where CONTAINER_ID is a unique identifier of this container (you can get this ID by running `sudo docker ps`). You can use this identifier to control your container and, in those cases, the first four characters are usually enough.
