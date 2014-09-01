# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'yaml'

if File.exists? 'local.yml'
  local_config = YAML.load_file 'local.yml'
else
  local_config = {}
end

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty32"

  config.vm.box_check_update = false

  # config.vm.network "forwarded_port", guest: 80, host: 8080
  if local_config.has_key? 'ports'
    local_config['ports'].each do |item|
      config.vm.network "forwarded_port", guest: item['guest'], host: item['host']
    end
  end

  # config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.network "public_network"

  # config.ssh.forward_agent = true

  # config.vm.synced_folder "../data", "/vagrant_data"
  if local_config.has_key? 'folders'
    local_config['folders'].each do |item|
      config.vm.synced_folder item['host'], item['guest']
    end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.hostname = 'vbox-nobelbiz'

  config.vm.provision "ansible" do |ans|
    ans.playbook = "provisioning/playbook.yml"
  end
end
