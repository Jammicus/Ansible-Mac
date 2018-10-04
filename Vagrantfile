# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure('2') do |config|

hostName="vagrant"
	config.vm.define "vagrant" do |instance|
		instance.vm.box = 'monsenso/macos-10.13'
		instance.vm.box_check_update=false
		instance.vm.hostname=hostName
		instance.vm.synced_folder ".", hostName, disabled: true

		config.vm.provider 'virtualbox' do |vb|
			vb.name = 'vagrant'
			vb.memory = '2048'
			vb.cpus = 1
			vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
			vb.customize ["modifyvm", :id, "--usb", "on"]
			vb.customize ["modifyvm", :id, "--usbehci", "off"]
			vb.customize [ "sharedfolder", "add", :id, "--name", hostName, "--hostpath", "/home/user/tmp/share", "--automount" ]
		end
	end
	#
	# Run Ansible from the Vagrant Hosts
	#
	# config.vm.provision "shell",
    # inline: "sudo mkdir -p /opt"

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "./vagrant.yml"
		ansible.limit = "all"
		ansible.verbose = "vv"
	end

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "./common.yml"
		ansible.limit = "all"
		ansible.verbose = "vv"
		ansible.extra_vars = {
			inventory_hostname: hostName
		}
	end

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "./platform.yml"
		ansible.limit = "all"
		ansible.verbose = "vv"
		ansible.extra_vars = {
			inventory_hostname: hostName,
			gnused_symlink: true,
			gnutar_symlink: true,
			openssl_symlink: true,
		}
	end

	# config.vm.provision "ansible" do |ansible|
	# 	ansible.playbook = "./frontend.yml"
	# 	ansible.limit = "all"
	# 	ansible.verbose = "vv"
	# end

	# config.vm.provision "ansible" do |ansible|
	# 	ansible.playbook = "./devops.yml"
	# 	ansible.limit = "all"
	# 	ansible.verbose = "vv"
	# end

	# config.vm.provision "ansible" do |ansible|
	# 	ansible.playbook = "./backend.yml"
	# 	ansible.limit = "all"
	# 	ansible.verbose = "vv"
	# end
end
