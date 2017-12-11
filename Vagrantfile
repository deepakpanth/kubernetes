# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "centos/7"

  config.vm.define "kube-01" do |kube|
    kube.vm.hostname = "kube-01"
    kube.vm.network "private_network", ip: "192.168.12.10"
    config.vm.provider :virtualbox do |vb|
       vb.customize ["modifyvm", :id, "--memory", "2048"]
       vb.customize ["modifyvm", :id, "--cpus", "2"]
    end  
    kube.vm.provision "shell", inline: $script
  end
 
 config.vm.define "kube-02" do |kube|
    kube.vm.hostname = "kube-02"
    kube.vm.network "private_network", ip: "192.168.12.11"
    config.vm.provider :virtualbox do |vb|
       vb.customize ["modifyvm", :id, "--memory", "2048"]
       vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
    kube.vm.provision "shell", inline: $script
  end

 config.vm.define "kube-03" do |kube|
    kube.vm.hostname = "kube-03"
    kube.vm.network "private_network", ip: "192.168.12.12"
    config.vm.provider :virtualbox do |vb|
       vb.customize ["modifyvm", :id, "--memory", "2048"]
       vb.customize ["modifyvm", :id, "--cpus", "1"]
    end
    kube.vm.provision "shell", inline: $script
  end

$script = <<SCRIPT
echo I am provisioning...
sudo cp /vagrant/hosts /etc/hosts

cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
setenforce 0
sudo yum install -y docker kubelet kubeadm kubectl kubernetes-cni
sudo systemctl enable docker.service && sudo systemctl start docker
sudo systemctl enable kubelet && sudo systemctl start kubelet

SCRIPT

end
