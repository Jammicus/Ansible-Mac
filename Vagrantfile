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
			default_user: "vagrant"
		}
	end

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "./platform.yml"
		ansible.limit = "all"
		ansible.verbose = "vv"
		ansible.extra_vars = {
			default_user: "vagrant",
			gnused_symlink: true,
			gnutar_symlink: true,
			openssl_symlink: true,
			install_python_two: true,
			libiconv_homebrew_install: true,
			wget_homebrew_install: true,
			python_two_homebrew_install: true,
			python_three_homebrew_install: true,
			maven_homebrew_install: true,
			doxygen_homebrew_install: true,
			cmake_homebrew_install: true,
		}
	end

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "./frontend.yml"
		ansible.limit = "all"
		ansible.verbose = "v"
		ansible.extra_vars = {
			default_user: "vagrant",
			yarn_homebrew_install: true,
			postman_homebrew_install: true,
			vscode_homebrew_install: true,
			yarn_homebrew_install: true
		}
	end

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "./devops.yml"
		ansible.limit = "all"
		ansible.verbose = "vv"
		ansible.extra_vars = {
			default_user: "vagrant",
			packer_homebrew_install: true
		}
	end

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "./backend.yml"
		ansible.limit = "all"
		ansible.verbose = "vv"
		ansible.extra_vars = {
			default_user: "vagrant",
			kotlin_homebrew_install: true
		}
	end
end