# K8s-Vagrant-Cluster
Vagrant | Kubernetes | Kubeadm


sudo kubeadm init --apiserver-advertise-address=192.168.50.10 --apiserver-cert-extra-sans=192.168.50.10 --node-name kube-master01 --pod-network-cidr=10.244.0.0/16

mkdir -p $HOME/.kube

sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

sudo chown $(id -u):$(id -g) $HOME/.kube/config

Add in all nodes with respective ips
sudo vim /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
Environment="KUBELET_EXTRA_ARGS=--node-ip=192.168.50.10"
