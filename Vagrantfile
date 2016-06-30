# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
     sudo yum update -y
     sudo yum install -y epel-release
     sudo yum install -y htop

     # glances
     sudo curl -L http://bit.ly/glances | /bin/bash

     # docker
     sudo curl -fsSL https://get.docker.com/ | sh
     sudo usermod -aG docker vagrant
     sudo systemctl enable docker.service && sudo systemctl start docker.service
     sudo docker pull mongo:latest    
     sudo docker pull nicolargo/glances   


     # mongodb
     sudo yum install -y mongodb-server mongodb
     sudo systemctl enable mongod && sudo systemctl start mongod

     # system tools
     sudo yum install -y strace ltrace sysstat atop lsof

     sudo sed -i "s/INTERVAL=600/INTERVAL=30/g" /etc/sysconfig/atop
     sudo systemctl enable atop && sudo systemctl start atop

     docker run -d mongo
     docker run -d mongo
     docker run -d -v /var/run/docker.sock:/var/run/docker.sock:ro --pid host --net host -it nicolargo/glances
     docker run -d -v /var/run/docker.sock:/var/run/docker.sock:ro --pid host --net host -it nicolargo/glances
     docker run -d -v /var/run/docker.sock:/var/run/docker.sock:ro --pid host --net host -it nicolargo/glances
     docker run -d -v /var/run/docker.sock:/var/run/docker.sock:ro --pid host --net host -it nicolargo/glances
  SHELL
end
