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
### vim kubernetes.repo
### dnf install kubeadm -y 
### systemctl enable kubelet
### systemctl start kubelet
### swapoff -a
### kubeadm init
### kubeadm config images pull
### systemctl restart docker
### systemctl start docker
### systemctl stop docker
### systemctl status docker.service
### dockerd --debug
### systemctl daemon-reload
### kubeadm config images pull --kubernetes-version=v1.28.2
### vim /etc/docker/daemon.json
