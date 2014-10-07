VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty32'

  config.vm.box_check_update = false

  config.user.defaults = {
    folders: [],
    ports:   [],
    vm: {
      memory: 2048,
      cpus: 1
    }
  }

  config.user.ports.each do |item|
    config.vm.network 'forwarded_port', guest: item['guest'], host: item['host']
  end

  config.ssh.forward_agent = true

  config.user.folders.each do |item|
    config.vm.synced_folder item['host'], item['guest']
  end

  config.vm.provider 'virtualbox' do |vb|
    vb.name   = 'vbox-nobelbiz'
    vb.cpus   = config.user.vm.cpus
    vb.memory = config.user.vm.memory
  end

  config.vm.hostname = 'vbox-nobelbiz'

  config.vm.provision 'ansible' do |ans|
    ans.playbook = 'provisioning/playbook.yml'
  end
end
