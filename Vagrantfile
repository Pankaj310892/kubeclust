# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "kubemaster" do |kubemaster|
    kubemaster.vm.hostname = "kubemaster"
    kubemaster.vm.box = "ubuntu/bionic64"
    kubemaster.vm.network "private_network", ip: "172.168.99.20"
    kubemaster.vm.provision "shell", path: "provision.sh"
    kubemaster.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
  end

  (1..2).each do |i|
    config.vm.define "worker#{i}" do |worker|
      worker.vm.hostname = "worker#{i}"
      worker.vm.box = "ubuntu/bionic64"
      worker.vm.network "private_network", ip: "172.168.99.2#{i}"
      worker.vm.provision "shell", path: "provision.sh"
      worker.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2
      end
    end
  end

end
