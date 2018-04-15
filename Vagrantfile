# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
#  config.vm.provider "virtualbox" do |vb|
# Display the VirtualBox GUI when booting the machine
#     vb.gui = true
#     vb.memory = "1024"
#  end
#  config.vm.synced_folder "./", "/ssDevOps"

  config.vm.define "oms" do |om|
    om.vm.box = "ubuntu/xenial64"
    ENV['LC_ALL']="en_US.UTF-8"
    om.vm.hostname = "oms"
#    ap.ssh.username = "vagrant"
#    ap.ssh.password = "vagrant"
    om.vm.network "forwarded_port", guest: 8080, host: 8080
    om.vm.network "forwarded_port", guest: 9990, host: 9990
    om.vm.network "forwarded_port", guest: 80, host: 8888
    om.vm.network "forwarded_port", guest: 8111, host: 8111
    om.vm.network :private_network, ip: "192.168.0.202"
    om.vm.synced_folder "./", "/oms"
    om.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.memory = "3072"
        vb.name = "oms"
    end
    om.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/playbook.yml"
        ansible.inventory_path = "ansible/inventory"
        ansible.become = true
        ansible.verbose = "vv"
    end
  end
end
