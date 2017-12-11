# kubernetes


### Initialization of Master:

This tutorial assumes **kube-01**  as the master and used kubeadm as a tool to install and setup the cluster. This section also assumes that you are using vagrant based setup provided along with this tutorial. If not, please update the IP address of the master accordingly.

To initialize master, run this on kube-01

```
kubeadm init --apiserver-advertise-address 192.168.12.10 --pod-network-cidr=192.168.0.0/16

```

```
[preflight] Some fatal errors occurred:
        /proc/sys/net/bridge/bridge-nf-call-iptables contents are not set to 1
        ## To fix this:  #echo '1' > /proc/sys/net/bridge/bridge-nf-call-iptables
        running with swap on is not supported. Please disable swap
        ## To fix this: #swapoff -a
[preflight] If you know what you are doing, you can skip pre-flight checks with `--skip-preflight-checks`
```

### Setup Kubectl (admin client)

On Master Node(kube-01)

```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

### Join other nodes to the K8s cluster (In this case kube-02 and kube-03)
Token is created while initializing the cluster with kubeadm

```
kubeadm join --token c04797.8db60f6b2c0dd078 192.168.12.10:6443 --discovery-token-ca-cert-hash sha256:88ebb5d5f7fdfcbbc3cde98690b1dea9d0f96de4a7e6bf69198172debca74cd0
```

### K8s Status Commands

```
kubectl get nodes

kubectl cluster-info

kubectl get pods -n kube-system

kubectl get events

```

### K8s cheat sheet
```
https://duckduckgo.com/?q=kubernetes+cheat+sheet&t=hf&ia=answer&iax=answer
```
