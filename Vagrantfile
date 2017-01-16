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
end
