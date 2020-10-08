# -*- mode: ruby -*-
# vi: set ft=ruby :

$num_instances = 3

Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"

  (1..$num_instances).each do |i|
    config.vm.define vm_name = "node#{i}" do |config|
      config.vm.hostname = "node#{i}"
      config.vm.network :private_network, ip: "172.17.177.#{i+20}" # ansible inventory

      if i == $num_instances
        config.vm.provision :ansible do |ansible|
          ansible.playbook       = "provision/playbook.yml"
          ansible.limit          = "all"
        end
      end
    end
  end

end
