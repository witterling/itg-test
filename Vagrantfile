# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  N = 3
  (1..N).each do |machine_id|
    config.vm.define "machine#{machine_id}" do |machine|
      machine.vm.box = "ubuntu/xenial64"
      machine.vm.network "private_network", ip: "192.168.17.#{99+machine_id}"
      machine.vm.hostname = "machine#{machine_id}"
      machine.vm.synced_folder ".", "/vagrant"
      machine.vm.provider "virtualbox" do |vb|
     	 vb.customize ["modifyvm", :id, "--name", "machine#{machine_id}"]
     	 vb.memory = "1024"
      end
      if machine_id == N
        machine.vm.provision :ansible do |ansible|
          # Disable default limit to connect to all the machines
          ansible.limit = "all"          
          ansible.playbook = "deploy-swarm.yml"
          ansible.groups = {
            "docker_swarm_manager" => ["machine1"],
            "docker_swarm_worker" => ["machine[2:3]"]
          }
        end
      end  
    end
  end
end