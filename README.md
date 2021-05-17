# Docker-fedora-34-nested-docker (* requires docker-ce)
from host

```
yum install qemu-img caja xorg-* mesa-* -y
```


* /sbin/init hooks the systemd pid 1 from host as --privileged

```

docker run -it -d --privileged=true --rm -e DISPLAY=$DISPLAY \
 --device /dev/kvm \
     --device /dev/snd \
-v /tmp/.X11-unix:/tmp/.X11-unix c4pt/fedora-34-docker-nested /sbin/init

docker exec -it <vm_hash> bash

docker-reload

```

Example of docker-nested-guest
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:ac:11:00:02  txqueuelen 0  (Ethernet)
        RX packets 793  bytes 124999 (122.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 691  bytes 5840971 (5.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 760  bytes 5863168 (5.5 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 760  bytes 5863168 (5.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
from Host
```
ssh -Y root@172.17.0.2
root passwd: Docker-fedora-34-nested-docker

[root@614f3461c819 ~]# caja
```

temp until new push

```
rm -rf /var/lib/docker/runtimes /var/lib/docker/runtimes-old
yum reinstall docker-ce -y
systemctl start docker

docker ps -a
```
default root passwd for fedora-34-nested
```
passwd for root : 

Docker-fedora-34-nested-docker

change with passwd 
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

