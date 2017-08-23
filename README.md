# Minecraft Spigot Server on Alpine Linux

This image provides a simple minecraft dedicated server based on spigot and oracles java. The image has
a size of about 167MB depending on the size of anapsix/alpine-java image and the build size of the 
latest spigot binary. 

## Quickstart
To run a simple spigot minecraft server do:

``` bash
docker run -it --rm -p 25565:25565 stenub/docker_alpine_spigot:latest
```

This starts a new minecraft server in interactive mode so that you have access to the server console. 
If you stop the container the generated world will be lost as it is in the nature of docker that
containers should be ephemeral. 

## Real Setup
To make the generated world persistent you have to mount a docker volume to 
the container.

``` bash
docker run -d --mount source=myvol1,target=/spigot -p 25565:25565 stenub/docker_alpine_spigot:latest
```

This starts a new container in background (or daemon) mode and binds local docker volume 'myvol1' to the
containers /spigot folder. Every change to the spigot server will be written to myvol1.
Please have a look at

``` bash
/var/lib/docker/volumes/myvol1/_data/
```
and you will find yourself comfortable with the known spigot config files. Edit them according to your
wishes and enjoy! ;-) 

## If Spigot is outdated

If the spigot-*.jar contained in the image is outdated, you can pm me/write email/open an issue on github
or generate a new image by getting the Dockerfile and building an image on your own. Just run

``` bash
docker build -t 'your_image_name'  .
```
in the folder in which you copied the Dockerfile. Don´t forget the dot or it won´t work! 
If you have problems or just want to say hello please drop me a message!
