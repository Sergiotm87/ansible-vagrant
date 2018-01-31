# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "debian/stretch64"
  config.vm.provider "virtualbox" do |provider|
    provider.memory = "512"
  end

N = 2
(1..N).each do |machine_id|
  config.vm.define "nodo#{machine_id}" do |machine|
    machine.vm.hostname = "nodo#{machine_id}"
    machine.vm.network :public_network,:bridge=>"br0"
    #machine.vm.network :public_network,ip: "192.168.1.20#{machine_id}"
    # Only execute once the Ansible provisioner,
    # when all the machines are up and ready.
    if machine_id == N
      machine.vm.provision :ansible do |ansible|
        # Disable default limit to connect to all the machines
        ansible.limit = "all"
        # Define ansible hosts
        ansible.groups = {
        "db-dns" => ["nodo1"],
        "web"  => ["nodo2"]
        }
        ansible.playbook = "playbook.yml"
      end
    end
  end
end
end
