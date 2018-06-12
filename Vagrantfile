# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|


  config.vm.define "catalyst" do |catalyst|
      catalyst.vm.box = "ubuntu/trusty64"
  end
  
   config.vm.network "forwarded_port", guest: 8888, host: 8888
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.network "public_network"

   config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI when booting the machine
     vb.gui = true
     vb.memory = "1024"
     vb.cpus ="2"
   end

    config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y python-dev
    sudo apt-get install -y python-pip
    sudo apt-get install -y ipython ipython-notebook
    sudo apt-get install -y python-numpy python-scipy python-matplotlib python-pandas python-sympy python-nose
    sudo pip install --upgrade ipython[all]
    sudo mkdir -p /vagrant/notebook
  SHELL

  config.vm.provision "shell", run: "always", inline: <<-SHELL
    ipython notebook --notebook-dir=/vagrant/notebook --ip=0.0.0.0 
  SHELL

end
