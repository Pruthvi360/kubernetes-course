## Kubectl master node installation
```
sudo apt install git -y
git clone https://github.com/Pruthvi360/kubernetes-course.git
cd kubernetes-course/kubernetes-installation/
chmod 777 setup-container.sh
./setup-container.sh
chmod 777 setup-kubetools.sh
sudo ./setup-kubetools.sh 
```
# Initializing the Kubernetes master
```
sudo kubeadm init
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml
kubectl apply -f kubernetes-course/kubernetes-installation/calico.yaml
kubectl cluster-info
kubectl get pods --all-namespaces
kubectl get pods
kubectl get nodes
```
