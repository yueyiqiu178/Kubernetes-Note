# Kubernetes-Note
## centos安裝kubernetes
### yum install -y kubelet kubeadm kubectl
### sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
### sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
### dnf -y upgrade
### dnf install https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.2.6-3.3.el7.x86_64.rpm
### yum install dnf-plugins-core
### dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
### dnf install docker-ce
### systemctl enable docker
### systemctl start docker
### vim /etc/yum.repos.d/kubernetes.repo
### dnf install kubeadm -y 
### systemctl enable kubelet
### systemctl start kubelet
### swapoff -a
### kubeadm init
### kubeadm config images pull
### vi /etc/containerd/config.toml
### systemctl restart containerd
### systemctl restart docker
### systemctl start docker
### systemctl stop docker
### systemctl status docker.service
### dockerd --debug
### systemctl daemon-reload
### kubeadm config images pull --kubernetes-version=v1.28.2
### vim /etc/docker/daemon.json
### vim /etc/selinux/config
### docker info | grep -i cgroup
### vim /etc/sysctl.d/k8s.conf
### export OS=CentOS_8
### export VERSION=1.23
### curl -L -o /etc/yum.repos.d/devel:kubic:libcontainers:stable.repo https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/$OS/devel:kubic:libcontainers:stable.repo
### curl -L -o /etc/yum.repos.d/devel:kubic:libcontainers:stable:cri-o:$VERSION.repo https://download.opensuse.org/repositories/devel:kubic:libcontainers:stable:cri-o:$VERSION/$OS/devel:kubic:libcontainers:stable:cri-o:$VERSION.repo
### dnf remove docker-ce
### dnf remove containerd.io
### dnf install cri-o
### systemctl daemon-reload
### systemctl enable --now crio
### systemctl status crio
### kubeadm config images pull
### hostnamectl set-hostname master01.tayeh.me
### dnf install firewalld
### systemctl enable firewalld
### systemctl start firewalld
### firewall-cmd --state
### firewall-cmd --get-default-zone
### firewall-cmd --get-active-zones
### firewall-cmd --list-all
### firewall-cmd --add-port={6443,2379-2380,10250,10251,10252,5473,179,5473}/tcp --permanent
### firewall-cmd --add-port={6443,2379-2380,10250,10251,10252,5473,179,5473}/tcp --permanent
### firewall-cmd --add-port={4789,8285,8472}/udp --permanent
### firewall-cmd --reload
### kubeadm init
### cd /etc/kubernetes/manifests
### rm -rf kubernetes
### systemctl status kubelet
### systemctl restart kubelet
### systemctl status kubelet
### curl http://localhost:10248/healthz
### systemctl status kubelet
### journalctl -f -u kubelet
### swapoff -a
### firewall-cmd --add-port={10250,30000-32767,5473,179,5473}/tcp --permanent
### firewall-cmd --add-port={4789,8285,8472}/udp --permanent
### firewall-cmd --reload
### docker info|grep Driver
### systemctl show --property=Environment kubelet |cat
### dnf install docker-ce --allowerasing
### dockerd --debug
### systemctl status docker.service
### journalctl -u docker.service
### systemctl stop firewalld
### systemctl show --property=Environment kubelet |cat
### crictl images
### crictl config runtime-endpoint unix:///var/run/containerd/containerd.sock
### crictl config image-endpoint unix:///var/run/containerd/containerd.sock

