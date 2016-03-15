desc 'run virtual machines for demo'
task 'machines' do
  exec 'vagrant up'
end

desc 'halt all virtual machines'
task 'halt_machines' do
  exec 'vagrant halt'
end

desc 'install zabbix server'
task 'install_server' do
  exec 'ansible-playbook -i inventory.cfg zabbix.yml'
end

desc 'install zabbix agent to all machines'
task 'install_agent' do
  exec 'ansible-playbook -i inventory.cfg zabbix-agent.yml'
end
