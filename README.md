# Docker-fedora-34-nested-docker (* requires docker-ce)

```

docker run -it -d --privileged=true --rm -e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix c4pt/fedora-34-docker-nested /sbin/init


yum reinstall docker-ce -y
systemctl start docker

docker ps -a

```
