# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
HOSTNAME = "mesos-cluster"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 4096
    vb.cpus = 2
  end  

  config.vm.define HOSTNAME do |machine|
    machine.vm.hostname = HOSTNAME
    machine.vm.network "private_network", ip: "10.42.15.11"
    machine.vm.provision "ansible" do |ansible|

      ansible.playbook = "./vagrant.yml"
      ansible.inventory_path = "./vagrant"
      ansible.raw_arguments = [ "-T 120", "--user=vagrant" ]

      ansible.extra_vars = {}

      ansible.verbose = "v"
      ansible.limit = "all"
    end
  end
end