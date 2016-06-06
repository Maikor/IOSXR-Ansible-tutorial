# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure(2) do |config|

  config.vm.provision "shell", inline: "echo Hello User"

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu/trusty64"
    ubuntu.vm.provision "file", source: "app_hosting/configs/ansible_env", destination:"/home/vagrant/ansible_env"
    ubuntu.vm.provision "file", source: "app_hosting/configs/ansible_hosts", destination:"/home/vagrant/ansible_hosts"

    ubuntu.vm.network :private_network, virtualbox__intnet: "link1", ip: "10.1.1.10"
    ubuntu.vm.provision :shell, path: "ubuntu.sh", privileged: false
  end

  config.vm.define "xr" do |xr|
    xr.vm.box = "xrv64"
    xr.vm.network :private_network, auto_config: false, virtualbox__intnet: "link1", ip: "10.1.1.20"
  end
   
end
