#
# Vagrant file to spin up:
#
# webserver (ansible host)
# workstation (for Chef) to setup knife
# chef (Chef server)
# node (chef node)
# jenkins (Jenkins server)
# dockerserver01, dockerserver02, dockerserver03
#
# vagrant up server
# vagrant ssh server
# vagrant halt server
# vagrant destroy server
#
# create quick default server:
#  vagrant init ubuntu/trusty64
#
Vagrant.configure("2") do |config|
  config.vm.define "webserver" do |webserver|
    webserver.vm.box = "ubuntu/trusty64"
    webserver.vm.network "private_network", ip: "192.168.0.2"
    webserver.vm.hostname = "webserver"
	#ansible.playbook = "nginx.yml"
  end
  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "ubuntu/trusty64"
    ansible.vm.network "private_network", ip:"192.168.0.254"
    ansible.vm.hostname = "ansible"
  end
  config.vm.define "workstation" do |workstation|
    workstation.vm.box = "ubuntu/trusty64"
    workstation.vm.network "private_network", ip:"192.168.0.252"
    workstation.vm.hostname = "workstation.example.com"
  end 
  config.vm.define "chef" do |chef|
    chef.vm.box = "ubuntu/trusty64"
    chef.vm.network "private_network", ip: "192.168.0.253"
    chef.vm.hostname = "chef.example.com"
    chef.vm.provider "virtualbox" do |v|
       v.memory = 4096
       v.cpus = 2
    end
  end
  config.vm.define "node" do |node|
    node.vm.box = "ubuntu/trusty64"
    node.vm.network "private_network", ip: "192.168.0.3"
    node.vm.hostname = "node.example.com"
    node.vm.provision "shell", inline: $script
  end  
  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "ubuntu/trusty64"
    jenkins.vm.network "private_network", ip:"192.168.0.252"
    jenkins.vm.hostname = "jenkins"
	jenkins.vm.provider "virtualbox" do |v|
		v.memory = 4096
		v.cpus = 2
	end
   end
  config.vm.define "dockerserver01" do |docker1|
    docker1.vm.box = "ubuntu/trusty64"
    docker1.vm.network "private_network", ip:"192.168.0.249"
    docker1.vm.hostname = "dockerserver01"
  end
  config.vm.define "dockerserver02" do |docker2|
    docker2.vm.box = "ubuntu/trusty64"
    docker2.vm.network "private_network", ip:"192.168.0.249"
    docker2.vm.hostname = "dockerserver02"
  end
  config.vm.define "dockerserver03" do |docker3|
    docker3.vm.box = "ubuntu/trusty64"
    docker3.vm.network "private_network", ip:"192.168.0.249"
    docker3.vm.hostname = "dockerserver03"
  end  
end
