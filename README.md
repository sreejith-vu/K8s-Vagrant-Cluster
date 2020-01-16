# K8s-Vagrant-Cluster
Vagrant | Kubernetes | Kubeadm

### On All Nodes Including Master

sudo vim /etc/systemd/system/kubelet.service.d/10-kubeadm.conf

Environment="KUBELET_EXTRA_ARGS=--node-ip=192.168.50.10"

sudo echo "Environment="KUBELET_EXTRA_ARGS=--node-ip=$(ifconfig |grep -A1 eth1 | grep inet | awk '{print $2}')"" >> /etc/systemd/system/kubelet.service.d/10-kubeadm.conf && sudo systemctl daemon-reload && sudo systemctl restart kubelet

sysctl net.bridge.bridge-nf-call-iptables=1

### Only in Master
sudo kubeadm init --apiserver-advertise-address=192.168.50.10 --apiserver-cert-extra-sans=192.168.50.10 --node-name kube-master01 --pod-network-cidr=10.244.0.0/16

mkdir -p $HOME/.kube

sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

sudo chown $(id -u):$(id -g) $HOME/.kube/config

Installing CNI
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
