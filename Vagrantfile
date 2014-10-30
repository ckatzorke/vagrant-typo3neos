# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.box = "hashicorp/precise64"
	
	config.ssh.forward_agent = true

	config.vm.network :private_network, ip: "192.168.23.4"

	config.vm.provision :shell, inline: 'sudo "echo 8.8.8.8	us.archive.ubuntu.com" >> /etc/hosts'

	config.vm.provision :chef_solo do |chef|
		chef.cookbooks_path = [ "cookbooks", "site-cookbooks" ]

		chef.log_level = :debug

		chef.add_recipe "typo3-neos"
		#chef.add_recipe "chef-oh-my-zsh"

		chef.json = {
			#'php' => {
			#	'directives' => {
			#		'date.timezone' => 'Europe/Berlin'
			#	}
			#}
			#:oh_my_zsh => {
			#	:users => ['vagrant']
			#}
		}
	end

	config.vm.provider "virtualbox" do |v|
        v.name = "TYPO3 Neos"
        v.customize ["modifyvm", :id, "--memory", "2048"]
	end
end