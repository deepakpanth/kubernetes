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
