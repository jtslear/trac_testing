# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos_base"
  config.vm.hostname = "jenkins-chef"
  config.vm.guest = "linux"
  config.vm.synced_folder "cookbooks", "/cookbooks"
  config.vm.synced_folder "chef", "/etc/chef"
  config.vm.provider "vmware_fusion" do |v|
  config.vm.network :forwarded_port, guest: 8080, host: 8080
#    v.gui = true
    v.vmx["memsize"] = "368"
    v.vmx["usb.vbluetooth.startConnected"] = "FALSE"
    v.vmx["tools.syncTime"] = "FALSE"
    v.vmx["hard-disk.hostBuffer"] = "disabled"
    v.vmx["annotation"] = "Testing a fix for trac recipe"
  end
  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "yum::epel"
    chef.add_recipe "trac"
  end
end
