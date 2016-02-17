# Project Calico

VxLan

Docker 1.9 or greater (details below)
ipset, iptables, and ip6tables kernel modules.

Run docker daemon with
--cluster-store=etcd://<ETCD IP>:2379


wget http://www.projectcalico.org/builds/calicoctl
chmod +x calicoctl

docker pull calico/node:latest
docker pull calico/node-libnetwork:latest


test local etcd
curl -L http://127.0.0.1:2379/version

on host 1:
sudo calicoctl node --libnetwork

on host 2:
sudo calicoctl node --libnetwork

on hosts on bare metal:
calicoctl pool add 192.168.0.0/16

docker network create --driver calico --subnet=192.168.0.0/24 net1

on hosts on cloud (AWS, DigitalOcean etc)
calicoctl pool add 192.168.0.0/16 --ipip --nat-outgoing

docker network create --driver calico --opt nat-outgoing=true --opt ipip=false --subnet=192.168.0.0/24 net1



on host 1:
docker run --net net1 --name workload-A -tid busybox

on host 2:
docker run --net net1 --name workload-B -tid busybox
docker inspect --format "{{ .NetworkSettings.Networks.net1.IPAddress }}" workload-B

on host 1:
docker exec workload-A ping -c 4 <IP address of B>
