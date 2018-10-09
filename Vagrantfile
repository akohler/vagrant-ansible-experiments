# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.box_version = "1804.02"
  #config.vm.network :forwarded_port, guest: 80, host: 4567
  config.vm.network "forwarded_port", guest: 80, host: 4567, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  
  # Run Ansible from the Vagrant VM  
  config.vm.provision "ansible_local" do |ansible|
    #ansible.playbook = "test_role.yml"
    ansible.playbook = "hello.yml"
    ansible.limit = "local"
    #ansible.verbose = true
    ansible.provisioning_path = "/vagrant/ansible"
    ansible.inventory_path = "/vagrant/ansible/inventory"
  end
end
