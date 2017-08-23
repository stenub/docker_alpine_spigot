# Minecraft Spigot Server on Alpine Linux

This image provides a simple minecraft dedicated server based on spigot and oracles java. The image has
a size of about 167MB depending on the size of anapsix/alpine-java image and the build size of the 
latest spigot binary. 

## Quickstart
To run a simple spigot minecraft server do:

``` bash
docker run -it --rm -p 25565:25565 stenub/docker_alpine_spigot:latest
```

This starts a new minecraft server in interactive mode so that you can access the server console. 
If you stop the container the generated world will be lost, as it iis in the nature of docker that
containers should be ephemeral. To make the generated world persistent you have to mount a docker volume to 
the container.

``` bash
docker run -d --mount source=myvol1,target=/spigot -p 25565:25565 stenub/docker_alpine_spigot:latest
```

This starts a new container and binds local docker volume myvol1 to the containers /spigot folder.
Every change to the spigot server will be written to myvol1. Please have a look in

``` bash
/var/lib/docker/volumes/myvol1/_data/
```
and you will find yourself comfortable with the known spigot config files. Edit them to according to your
wishes and enjoy! ;-) 
