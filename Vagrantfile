# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "generic/centos7"

  config.vm.define "m1" do |machine|
    machine.vm.network "private_network", ip: "10.0.10.10"
    machine.vm.hostname = "m1"
  end
 
  config.vm.define "m2" do |machine|
    machine.vm.network "private_network", ip: "10.0.10.11"
    machine.vm.hostname = "m2"
  end

  config.vm.define "i1" do |machine|
    machine.vm.network "private_network", ip: "10.0.10.12"
    machine.vm.hostname = "i1"
  end
 
  config.vm.define "i2" do |machine|
    machine.vm.network "private_network", ip: "10.0.10.13"
    machine.vm.hostname = "i2"
  end
 
  config.vm.define "dashboards1" do |machine|
    machine.vm.network "private_network", ip: "10.0.10.14"
    machine.vm.hostname = "dashboards1"
  end
 
  config.vm.define 'controller' do |machine|
    machine.vm.network "private_network", ip: "10.0.10.15"
    machine.vm.synced_folder ".", "/vagrant", mount_options: ["dmode=700,fmode=700"]
    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook          = "/vagrant/ansible-playbook/opensearch.yml"
      ansible.verbose           = true
      ansible.install           = true
      ansible.sudo              = true
      ansible.limit             = "all" # or only "nodes" group, etc.
      ansible.inventory_path    = "/vagrant/inventories/opensearch"
    end
  end
end
