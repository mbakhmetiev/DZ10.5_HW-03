# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 5432, host: 15432, host_ip: "127.0.0.1"
  config.vm.provider "virtualbox" do |vb| 
  config.vm.define "postgres_ubuntu_16_04"
    vb.memory = "2048"    
    vb.gui = false
  end
  
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    sudo apt install build-essential libreadline-dev zlib1g-dev -y
    wget https://ftp.postgresql.org/pub/source/v8.4.22/postgresql-8.4.22.tar.gz
    tar -xzvf postgresql-8.4.22.tar.gz
    cd postgresql-8.4.22/
    sudo mkdir /opt/PostgreSQL
    ./configure --prefix=/opt/PostgreSQL
    make
    sudo make install
  SHELL
end
