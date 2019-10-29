# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|

	NodeName = "maxis-devops-ubuntu"

	config.vm.define NodeName do |node|
	  node.vm.box = "ubuntu/bionic64"
	  node.vm.hostname = "#{NodeName}.example.com"
	  node.vm.network "private_network", ip: "172.42.42.101"
	  node.ssh.forward_agent = true
	  
	  node.vm.network "forwarded_port", guest: 8080, host: 7001   # jenkins
	  node.vm.network "forwarded_port", guest: 8090, host: 18090   # Internal app
	  node.vm.synced_folder "vagrant-data", "/home/vagrant-data"
	  
	  node.vm.provider "virtualbox" do |v|
		v.name = NodeName
		v.memory = 2048
		v.cpus = 1
		v.gui = false
	  end
	end

	config.vm.provision :shell, :path => "vagrant-docker-vm-init.sh"
	  
end
