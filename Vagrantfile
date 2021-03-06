# -*- mode: ruby -*-
# vi: set ft=ruby :
ENV["LC_ALL"] = "zh_CN.UTF-8"
Vagrant.configure("2") do |config|
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/xenial64"
  
  config.vm.provider "virtualbox" do |vb|

    # Display the VirtualBox GUI when booting the machine
    vb.gui = false

    # Customize any other parameters
    vb.customize [
      'modifyvm',                :id,
      '--memory',                '512',
      '--cpus',                  '2',
      '--paravirtprovider',      'kvm', # can be set to "paravirt"
      '--ioapic',                'on', # turn on I/O APIC
      '--natdnsproxy1',          'on',
      '--natdnshostresolver1',   'on']
  #
  end
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
   config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

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

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:


  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  config.vm.define "consul-001" do |web|
    web.vm.hostname = "consul-001.vagrant"
    web.vm.network "private_network", ip: "192.168.30.11"
  end

  config.vm.define "consul-002" do |web|
    web.vm.hostname = "consul-002.vagrant"
    web.vm.network "private_network", ip: "192.168.30.20"
  end

  config.vm.define "consul-003" do |web|
    web.vm.hostname = "consul-003.vagrant"
    web.vm.network "private_network", ip: "192.168.30.30"
  end

  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", path: "./install_consul.server.sh"
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
