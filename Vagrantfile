# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
 config.vm.box_check_update = "false"
 config.vm.provider "virtualbox" do |vb|
   vb.memory = "4048"
   vb.cpus = 2
 end

 config.vm.define "webserver" do |web|
   web.vm.hostname = "dev.project.com"
   web.vm.box = "generic/debian10"
   web.vm.network :private_network, ip: "77.21.10.10"
   web.vm.network "forwarded_port", guest: "80", host: "8080"
   web.vm.synced_folder ".", "/srv/www/project/", type: "nfs"
   config.vm.provision :ansible do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "build/ansible/provisioning/webserver.yml"
   end
  end
end


