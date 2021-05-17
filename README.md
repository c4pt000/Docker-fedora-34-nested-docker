# Docker-fedora-34-nested-docker (* requires docker-ce)

* /sbin/init hooks the systemd pid 1 from host as --privileged

```

docker run -it -d --privileged=true --rm -e DISPLAY=$DISPLAY \
 --device /dev/kvm \
     --device /dev/snd \
-v /tmp/.X11-unix:/tmp/.X11-unix c4pt/fedora-34-docker-nested /sbin/init

docker exec -it <vm_hash> bash

docker-reload

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

```
passwd for root : 

Docker-fedora-34-nested-docker
```


cd /usr/bin
yum install wget -y
wget https://raw.githubusercontent.com/c4pt000/Docker-fedora-34-nested-docker/main/xhost-gen

chmod +x /usr/bin/xhost-gen

xhost-gen
```

SSH forwarding from docker-nested guest
```
yum install openssh-server net-tools -y
yum install passwd cracklib-dicts -y

"set passwd"

passwd
cd /etc/ssh
mv sshd_config sshd_config.orig
wget https://raw.githubusercontent.com/c4pt000/Docker-fedora-34-nested-docker/main/sshd_config
systemctl restart sshd
```
   
 then ssh -Y root@172.17.0.7                          where root@172.17.0.7 is the ip of the nested docker guest from ifconfig
using freshly made passwd for docker-nested guest

