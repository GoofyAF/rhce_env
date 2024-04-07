# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Base VM OS configuration.
  config.vm.box = "generic/rhel9"
  config.ssh.insert_key = false
  config.vm.synced_folder '.', '/vagrant', disabled: true

  # General VirtualBox VM configuration.
  config.vm.provider :virtualbox do |v|
    v.memory = 512
    v.cpus = 1
    v.linked_clone = true
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  # utility.
  config.vm.define "utility" do |utility|
    utility.vm.hostname = "utility.lab.example.com"
    utility.vm.network :private_network, ip: "192.168.56.8"
    utility.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # workstation.
  config.vm.define "workstation" do |workstation|
    workstation.vm.hostname = "workstation.lab.example.com"
    workstation.vm.network :private_network, ip: "192.168.56.9"
    workstation.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # servera.
  config.vm.define "servera" do |servera|
    servera.vm.hostname = "servera.lab.example.com"
    servera.vm.network :private_network, ip: "192.168.56.10"
    servera.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # serverb.
  config.vm.define "serverb" do |serverb|
    serverb.vm.hostname = "serverb.lab.example.com"
    serverb.vm.network :private_network, ip: "192.168.56.11"
    serverb.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # serverc.
  config.vm.define "serverc" do |serverc|
    serverc.vm.hostname = "serverc.lab.example.com"
    serverc.vm.network :private_network, ip: "192.168.56.12"
    serverc.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # serverd.
  config.vm.define "serverd" do |serverd|
    serverd.vm.hostname = "serverd.lab.example.com"
    serverd.vm.network :private_network, ip: "192.168.56.13"
    serverd.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end
  # Ansible provisioning.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "configure.yml"
    #ansible.become = true
    ansible.limit = "all"
    ansible.extra_vars = {
      ansible_python_interpreter: "/usr/bin/python3",
      ansible_user: 'vagrant',
      ansible_ssh_private_key_file: "~/.vagrant.d/insecure_private_key",
    }  
  end
end