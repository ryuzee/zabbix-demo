# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  box_name = 'opscode-ubuntu-14.04'
  log_level = 'v'

  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end

  config.vm.define 'mysql-server'.to_sym do |mysql|
    mysql.vm.box = box_name
    mysql.vm.hostname = 'mysql-server'
    mysql.vm.network 'private_network', ip: '192.168.44.50'
    mysql.vm.provision 'ansible' do |ansible|
      ansible.verbose = log_level
      ansible.limit = 'all'
      ansible.playbook = 'mysql-server.yml'
      ansible.inventory_path = 'inventory.cfg'
    end
  end

  config.vm.define 'zabbix-server'.to_sym do |server|
    server.vm.box = box_name
    server.vm.hostname = 'zabbix-server'
    server.vm.network 'private_network', ip: '192.168.44.10'
    server.vm.provision 'ansible' do |ansible|
      ansible.verbose = log_level
      ansible.limit = 'all'
      ansible.playbook = 'zabbix-server.yml'
      ansible.inventory_path = 'inventory.cfg'
    end
  end

  N = 2
  (1..N).each do |i|
    config.vm.define "zabbix-client#{i}".to_sym do |client|
      client.vm.box = box_name
      client.vm.hostname = "zabbix-client#{i}"
      client.vm.network 'private_network', ip: "192.168.44.#{100 + i}"
      client.vm.provision 'ansible' do |ansible|
        ansible.verbose = log_level
        ansible.limit = "zabbix-client#{i}"
        ansible.playbook = 'client.yml'
        ansible.inventory_path = 'inventory.cfg'
      end
    end
  end
end
