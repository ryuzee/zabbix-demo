# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  box_name = 'opscode-ubuntu-14.04'

  config.vm.define :server do |server|
    server.vm.box = box_name
    server.vm.hostname = 'zabbix-server'
    server.vm.network "private_network", ip: "192.168.44.10"
  end

  config.vm.define :mysql do |mysql|
    mysql.vm.box = box_name
    mysql.vm.hostname = 'zabbix-server'
    mysql.vm.network "private_network", ip: "192.168.44.50"
  end

  2.times do |i|
    config.vm.define "client#{i+1}".to_sym do |client|
      client.vm.box = box_name
      client.vm.hostname = "zabbix-client#{i+1}"
      client.vm.network "private_network", ip: "192.168.44.#{101 + i}"
    end
  end
end
