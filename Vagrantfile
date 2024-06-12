
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
      # server.ssh.insert_key = false
      # server.ssh.username = "vagrant"
      # server.ssh.password = "vagrant"
      # server.vm.provision "shell", inline: <<-'SHELL' 
      #   sed -i 's/^#* *\(PermitRootLogin\)\(.*\)$/\1 yes/' /etc/ssh/sshd_config
      #   systemctl restart sshd.service
      # SHELL
    end
  end

  # config.vm.define "server2" do |server2|
  #   server2.vm.box = "ubuntu/xenial64"
  #   server2.vm.network "private_network", ip: "192.168.56.12"
  #   server2.vm.network "public_network"
    # server2.ssh.insert_key = false
    # server2.ssh.username = "vagrant"
    # server2.ssh.password = "vagrant"
    # config.vm.provision "shell", inline: <<-'SHELL' 
    #   sed -i 's/^#* *\(PermitRootLogin\)\(.*\)$/\1 yes/' /etc/ssh/sshd_config
    #   systemctl restart sshd.service
    # SHELL
  # end

  # config.vm.define "server3" do |server3|
  #   server3.vm.box = "ubuntu/xenial64"
  #   server3.vm.network "private_network", ip: "192.168.56.13"
  #   server3.vm.network "public_network"
    # server3.ssh.insert_key = false
    # server3.ssh.username = "vagrant"
    # server3.ssh.password = "vagrant"
    # config.vm.provision "shell", inline: <<-'SHELL' 
    #   sed -i 's/^#* *\(PermitRootLogin\)\(.*\)$/\1 yes/' /etc/ssh/sshd_config
    #   systemctl restart sshd.service
    # SHELL
  # end
  
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
