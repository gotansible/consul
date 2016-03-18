# -*- mode: ruby -*-
# vi: set ft=ruby :

system("
    if [ #{ARGV[0]} = 'up' ]; then
        echo 'You are doing vagrant up and can execute your script'
        ansible-galaxy install -r requirements.yml --force
    fi
")

Vagrant.configure(2) do |config|
	config.vm.define "server" do |server|
		server.vm.box = "hashicorp/precise64"
		server.vm.hostname = "server"
		server.vm.provision :ansible do |ansible|
			ansible.playbook = "server.yml"
		end
		server.vm.network "private_network", ip: "192.168.50.4"
	end

	config.vm.define "client" do |client|
		client.vm.box = "hashicorp/precise64"
		client.vm.hostname = "client"
		client.vm.provision :ansible do |ansible|
			ansible.playbook = "client.yml"
		end
		client.vm.network "private_network", ip: "192.168.50.5"
	end
end
