VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty32'

  config.vm.box_check_update = false

  config.user.defaults = {
    hostname: 'vbox-nobelbiz',
    folders: [],
    ports:   [],
    networks: {
        private: []
    },
    vm: {
      cpus: 1,
      memory: 1024,
      name: 'vbox-nobelbiz'
    }
  }

  config.user.ports.each do |item|
    config.vm.network 'forwarded_port', guest: item['guest'], host: item['host']
  end

  config.user.networks.private.each do |item|
    config.vm.network 'private_network', ip: item['ip_address']
  end

  config.ssh.forward_agent = true

  config.user.folders.each do |item|
    config.vm.synced_folder item['host'], item['guest']
  end

  config.vm.provider 'virtualbox' do |vb|
    vb.name   = config.user.vm.name
    vb.cpus   = config.user.vm.cpus
    vb.memory = config.user.vm.memory
  end

  config.vm.hostname = config.user.hostname

  config.vm.provision 'ansible' do |ans|
    ans.playbook = 'provisioning/playbook.yml'
  end
end
