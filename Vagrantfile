# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
	config.vm.define "server" do |server|
		server.vm.box = "hashicorp/precise64"
		server.vm.provision :ansible do |ansible|
			ansible.playbook = "server.yml"
		end
		server.vm.network "private_network", ip: "192.168.50.4"
	end

	config.vm.define "client" do |client|
		client.vm.box = "hashicorp/precise64"
		client.vm.provision :ansible do |ansible|
			ansible.playbook = "client.yml"
		end
		client.vm.network "private_network", ip: "192.168.50.5"
	end
end
