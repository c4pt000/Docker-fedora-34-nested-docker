# Docker-fedora-34-nested-docker (* requires docker-ce)

```

docker run -it -d --privileged=true --rm -e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix c4pt/fedora-34-docker-nested /sbin/init

systemctl start docker

docker ps -a

```


temp until new push

```
rm -rf /var/lib/docker/runtimes /var/lib/docker/runtimes-old
yum reinstall docker-ce -y
systemctl start docker

docker ps -a
```
