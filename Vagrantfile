
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.define "ansiblesrv" do |ansiblesrv|
    ansiblesrv.vm.box = "ubuntu/xenial64"
    ansiblesrv.vm.network "private_network", ip: "192.168.56.10"
    ansiblesrv.vm.network "public_network"
    ansiblesrv.vm.provision :ansible_local do |ansible|
      ansible.verbose = true
      ansible.install = true
      ansible.limit = "servers"
      ansible.playbook = "playbook.yml"
      ansible.inventory_path = "inventory.ini"
    end
  end
  
  N = 3
  (1..N).each do |server_id|
    config.vm.define "server#{server_id}" do |server|
      server.vm.box = "ubuntu/xenial64"
      server.vm.network "private_network", ip: "192.168.56.#{10+server_id}"
      server.vm.network "public_network"
    end
  end

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.
end
