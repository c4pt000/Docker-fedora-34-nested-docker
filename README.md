# Docker-fedora-34-nested-docker (* requires docker-ce)

```

docker run -it -d --privileged=true --rm -e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix c4pt/fedora-34-docker-nested /sbin/init

docker exec -it <vm_hash> bash

cd /usr/bin
yum install wget -y
wget https://raw.githubusercontent.com/c4pt000/Docker-fedora-34-nested-docker/main/xhost-gen

chmod +x /usr/bin/xhost-gen

systemctl start docker

docker ps -a

```


temp until new push

```
rm -rf /var/lib/docker/runtimes /var/lib/docker/runtimes-old
yum reinstall docker-ce -y
systemctl start docker

docker ps -a


cd /usr/bin
yum install wget -y
wget https://raw.githubusercontent.com/c4pt000/Docker-fedora-34-nested-docker/main/xhost-gen

chmod +x /usr/bin/xhost-gen

xhost-gen
```
