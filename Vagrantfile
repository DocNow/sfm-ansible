# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 4096
    vb.cpus =2
  end

  # sfmdocker VM
  config.vm.define "sfmdocker" do |sfmdocker|
    sfmdocker.vm.hostname = "sfmdocker"
    sfmdocker.vm.box = "ubuntu/trusty64"
    sfmdocker.vm.network :private_network, ip: "192.168.33.10"
  end

  # ssh settings
  config.ssh.insert_key = false

  # Ansible provision

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "ansible/site.yml"
    ansible.sudo = true
    ansible.verbose = ""
  end

end
