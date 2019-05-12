# This guide is optimized for Vagrant 1.7 and above.
Vagrant.require_version ">= 1.7.0"

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
end

  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/id_rsa.pub"
  config.vm.provision "shell", inline: "cat ~vagrant/.ssh/id_rsa.pub >> ~vagrant/.ssh/authorized_keys"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "create-k8scluster.yaml"
  end
end
