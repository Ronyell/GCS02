# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

  config.vm.define "db" do |db|
    db.vm.box = "ubuntu/trusty64"
    db.vm.network "forwarded_port", guest: 5432, host: 5432, host_ip: "192.168.1.11"
    db.vm.network "private_network", ip: "192.168.1.11"

    db.vm.provider "virtualbox" do |vb1|
      vb1.name = "dj-database"
      vb1.gui = false
      vb1.memory = "512"
      vb1.cpus = 1
    end

    db.vm.provision "shell", path: "scriptdb.sh"
  end

  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/trusty64"
    web.vm.network "forwarded_port", guest:8000, host:8000, host_ip: "192.168.1.10"
    web.vm.network "private_network", ip: "192.168.1.10"

    web.vm.provider "virtualbox" do |vb2|
      vb2.name = "dj"
      vb2.gui = false
      vb2.memory = "512"
      vb2.cpus = 1
    end

    web.vm.provision "shell", path: "scriptweb.sh"

  end
end
