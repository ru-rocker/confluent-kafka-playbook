# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.vm.box_check_update = false

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
  end

  config.vm.define "node1" do |node1|
    node1.vm.hostname = "node1"
    node1.vm.network "private_network", ip: "172.20.20.10"
  end
  # End node1

  config.vm.define "node2" do |node2|
    node2.vm.hostname = "node2"
    node2.vm.network "private_network", ip: "172.20.20.20"
  end
  # End node2

  config.vm.define "node3" do |node3|
    node3.vm.hostname = "node3"
    node3.vm.network "private_network", ip: "172.20.20.30"
  end
  # End node3

end
