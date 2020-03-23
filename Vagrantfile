# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'socket'

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
  config.vm.box = "centos/8"
  config.vm.box_version = "1905.1"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false
 
  # Create a forwarded port that is accessible only to the host machine
  # 8545 -> GETH RPC Port
  # 8546 -> GETH WS Port
  # 3306 -> Mysql Port 
  config.vm.network "forwarded_port", guest: 8546, host: 8546, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 8545, host: 8545, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 3306, host: 3306, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/vagrant"

  config.ssh.private_key_path = "/home/christian/VirtualBox VMs/go-ethereum/private_key" if "#{`hostname`[0..-2]}".eql?("christian-P65xHP")  

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.memory = "4096"
  end
 
  # See https://github.com/hashicorp/vagrant/issues/11299 
  config.vm.provision "shell", inline: "dnf install -y python3-pip && pip3 install --upgrade ansible==2.7.13"

  config.vm.provision "ansible_local" do |ansible|
    ansible.install = false
    ansible.playbook = "provisioning/playbook.yml"
    ansible.install_mode = "pip"
    ansible.version = "2.7.13"
    ansible.compatibility_mode = "2.0"
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
  end  

end
