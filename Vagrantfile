# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_API_VERSION = "2"
Vagrant.configure(VAGRANT_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.ssh.insert_key = false
  config.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']

  # build host
  config.vm.define "build-host" do |build|

    build.vm.hostname = "build.host"
    build.vm.network :private_network, ip: "192.168.60.7"

    build.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      ansible.inventory_path = "provisioning/inventory"
      ansible.limit = "all"
    end
  end
end
