#
# Vagrant file to spin up
# Ansible server
# Webserver (ansible host)
# Workstation (for Chef) to setup knife
#
# vagrant up ansible
# vagrant up webserver
# vagrant up workstation
#
# vagrant ssh ansible
# vagrant ssh webserver
# vagrant ssh workstation
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
  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "ubuntu/trusty64"
    jenkins.vm.network "private_network", ip:"192.168.0.252"
    jenkins.vm.hostname = "jenkins"
	jenkins.vm.provider "virtualbox" do |v|
		v.memory = 4096
		v.cpus = 2
	end
   end
  config.vm.define "dockerserver01" do |docker|
    docker.vm.box = "ubuntu/trusty64"
    docker.vm.network "private_network", ip:"192.168.0.249"
    docker.vm.hostname = "dockerserver01"
  end    
end
