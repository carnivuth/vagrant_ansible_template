Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/jammy64'
  config.ssh.insert_key = true

  config.vm.provider "virtualbox" do |v|
#    v.linked_clone = true
    v.memory = 6144
    v.cpus = 4
  end

  # edgex runtime node
  config.vm.define 'main' do |machine|
    machine.vm.hostname = 'main'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2221, guest: 22
    machine.vm.network 'forwarded_port', host: 8080, guest: 80, protocol: "tcp"
    machine.vm.network 'private_network', virtualbox__intnet: 'cluster', ip: '10.0.0.10'
  end

  config.vm.define 'cluster-node-1' do |machine|
    machine.vm.hostname = 'cluster-node-1'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2222, guest: 22
    machine.vm.network 'private_network', virtualbox__intnet: 'cluster', ip: '10.0.0.20'
  end

  config.vm.define 'cluster-node-2' do |machine|
    machine.vm.hostname = 'cluster-node-2'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2223, guest: 22
    machine.vm.network 'private_network', virtualbox__intnet: 'cluster', ip: '10.0.0.30'
  end

  config.vm.define 'cluster-node-3' do |machine|
    machine.vm.hostname = 'cluster-node-3'
    machine.vm.network 'forwarded_port', id: 'ssh', host: 2224, guest: 22
    machine.vm.network 'private_network', virtualbox__intnet: 'cluster', ip: '10.0.0.40'
  end

end
