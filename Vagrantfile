# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  standard_machine config, 'summerschool.react'
end

def standard_machine(config, hostname)
  config.vm.define hostname do |config|

    ### MACHINE CONFIGURATION
    config.vm.box = "debian/contrib-jessie64"
    config.vm.network :public_network
    config.vm.hostname = hostname
    config.ssh.insert_key = false
    config.vm.synced_folder './provisioning', '/vagrant/provisioning', mount_options: ["fmode=666"]
    #config.vm.synced_folder "opt/", "/opt/tinker", create: true

    config.vm.provider "virtualbox" do |vb|
      vb.customize ['modifyvm', :id, '--nictype1', 'virtio']
      vb.customize ['modifyvm', :id, '--nictype2', 'virtio']
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      vb.memory = 2048
      vb.cpus   = 2
    end

    ### PROVISIONING
    config.vm.provision "ansible_local" do |ansible|
      ansible.install  = true
      ansible.playbook = "provisioning/site.yml"
      ansible.provisioning_path = "/vagrant"
      ansible.inventory_path = "provisioning/hosts"
      ansible.verbose = true
    end

    yield(config) if block_given?
  end
end
