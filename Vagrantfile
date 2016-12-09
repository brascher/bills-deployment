# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Please don't change it unless you know what you're doing.
VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.8.1"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 4
  end

  config.vm.provision :shell, inline: "cat /vagrant/hosts > /etc/hosts"
  config.vm.provision :shell, path: "ubuntu-with-ansible.sh"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "C:\\dev\\project_name", "/opt/project_name"

  # Set up machine
  config.vm.define "dev-machine", primary: true do |node|
    node.vm.box = "ubuntu/trusty64"
    node.vm.hostname = "dev-machine"
    node.vm.network "private_network", ip: "192.168.33.150"
  end

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

end
