#############################################################
#                                                           #
#   Vagrantfile for Ansible for Sberbank Open Data Demo     #
#                                                           #
#   The following providers are supported:                  #
#    - VirtualBox                                           #
#                                                           #
#############################################################

require './reboot-plugin'

Vagrant.configure("2") do |config|
  config.vm.define "sberbank-opendata" do |host|

    # General settings for virtual machine
    host.vm.box = "centos/7"
    host.vm.hostname = "sberbank-opendata"
    host.vm.network "private_network", ip: "10.0.4.10"

    # Shared folder with input data
    host.vm.synced_folder "data", "/home/vagrant/opendata/input", type: "virtualbox"

    # Forward port for Kibana
    host.vm.network "forwarded_port", guest: 5601, host: 5601

    # Provisioning dependencies
    host.vm.provision "ansible_local" do |ansible|
      ansible.install_mode = "pip"
      ansible.playbook = "provisioning/dependencies.yml"
      ansible.verbose = "v"
    end

    # Reboot machine
    host.vm.provision "unix_reboot"

    # Provisioning Docker images
    host.vm.provision "ansible_local" do |ansible|
      ansible.install_mode = "pip"
      ansible.playbook = "provisioning/images.yml"
      ansible.verbose = "v"
    end

    # Resources settings
    host.vm.provider "virtualbox" do |v|
      v.cpus = 2
      v.memory = 4096
    end
  end
end
