# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  config.vm.box = "ubuntu/jammy64"
  config.vm.boot_timeout = 900

  # Define a method for configuring a VM
  def configure_vm(vm, memory, cpus)
    vm.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = memory
      vb.cpus = cpus
    end
  end

  # master01
  config.vm.define "master01" do |master01|
    master01.vm.hostname = "master01"
    master01.vm.network :private_network, ip: "10.0.0.11"
    configure_vm(master01, "2048", 2)
  end

  # master02
  config.vm.define "master02" do |master02|
    master02.vm.hostname = "master02"
    master02.vm.network :private_network, ip: "10.0.0.12"
    configure_vm(master02, "2048", 2)
  end

  # master03
  config.vm.define "master03" do |master03|
    master03.vm.hostname = "master03"
    master03.vm.network :private_network, ip: "10.0.0.13"
    configure_vm(master03, "2048", 2)
  end

  # worker01
  config.vm.define "worker01" do |worker01|
    worker01.vm.hostname = "worker01"
    worker01.vm.network :private_network, ip: "10.0.0.21"
    configure_vm(worker01, "1024", 2)
  end

  # worker02
  config.vm.define "worker02" do |worker02|
    worker02.vm.hostname = "worker02"
    worker02.vm.network :private_network, ip: "10.0.0.22"
    configure_vm(worker02, "1024", 2)
  end

  # loadbalancer
  config.vm.define "lb" do |lb|
    lb.vm.hostname = "lb"
    lb.vm.network :private_network, ip: "10.0.0.10"
    configure_vm(lb, "1024", 2)
  end

  ### External shell scripts for configuration
  # - Run on every node
  config.vm.provision "bootstrap", type: "shell" do |script|
    script.path = "./bash/bash.sh"
  end
end





  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false


  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080


  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"


  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"


  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"


  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"


  # Disable the default share of the current code directory. Doing this
  # provides improved isolation between the vagrant box and your host
  # by making sure your Vagrantfile isn't accessible to the vagrant box.
  # If you use this you may want to enable additional shared subfolders as
  # shown above.
  # config.vm.synced_folder ".", "/vagrant", disabled: true


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


  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
