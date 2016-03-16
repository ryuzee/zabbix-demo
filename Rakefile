task 'all' do
  ['install_mysql', 'install_server', 'install_agent'].each do |t|
    Rake::Task[t].invoke
  end
end

desc 'run virtual machines for demo'
task 'machines' do
  system 'vagrant up'
end

desc 'halt all virtual machines'
task 'halt_machines' do
  system 'vagrant halt'
end

desc 'install zabbix server'
task 'install_server' do
  system 'ansible-playbook -i inventory.cfg zabbix.yml'
end

desc 'install zabbix agent to all machines'
task 'install_agent' do
  system 'ansible-playbook -i inventory.cfg zabbix-agent.yml'
end

desc 'install mysql server'
task 'install_mysql' do
  system 'ansible-playbook -i inventory.cfg mysql.yml'
end
