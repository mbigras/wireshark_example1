machines = [
  { 'name' => 'aci', 'address' => '192.168.33.10' },
  { 'name' => 'bop', 'address' => '192.168.33.11' },
]

Vagrant.configure('2') do |config|
  config.ssh.insert_key = false
  machines.each do |machine|
    config.vm.define machine['name'] do |v|
      v.vm.box = 'bento/ubuntu-16.04'
      v.vm.hostname = machine['name']
      v.vm.network 'private_network', ip: machine['address']
    end
  end
end
