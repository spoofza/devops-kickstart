# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = "devops"
  config.vm.box = "ubuntu/bionic64"
  config.vm.box_version = "20180509.0.0"
  config.vm.box_check_update = false
  config.vm.box_url = "https://vagrantcloud.com/ubuntu/bionic64"
  config.vm.network :forwarded_port, guest: 80, host: 8080, id: "HTTP80", protocol: "tcp", auto_correct: true

  config.vm.define :devops do |devops|

  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "4096"
    vb.cpus = 2
    vb.name = "devops"
    vb.linked_clone = true
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    vb.customize [ "guestproperty", "set", :id, "/VirtualBox/GuestAdd/VBoxService/--timesync-set-threshold", 10000 ]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.install = true
    ansible.verbose = true
    ansible.install_mode = "pip"
    ansible.version = "2.4.4.0"
    ansible.provisioning_path = "/vagrant/ansible"
    ansible.galaxy_role_file = "/vagrant/ansible/requirements.yml"
  end
end
