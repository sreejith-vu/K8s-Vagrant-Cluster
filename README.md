# K8s-Vagrant-Cluster
Vagrant | Kubernetes | Kubeadm


sudo kubeadm init --apiserver-advertise-address=192.168.50.10 --apiserver-cert-extra-sans=192.168.50.10 --node-name kube-master01 --pod-network-cidr=10.244.0.0/16
