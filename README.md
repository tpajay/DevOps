# DevOps
DevOps / Configuration Management / Continuous Integration repo.  This respository is for anything related.  VirtualBox ~ Vagrant ~ Ansible ~ Chef ~ Jenkins ~ Docker ~ Kubernetes


<b>NOTES: Docker Swarm</b>

	
	Install Docker Machine:
	sudo curl -L https://github.com/docker/machine/releases/download/v0.9.0/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine && chmod +x /tmp/docker-machine && sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
	docker-machine -ls (to list machines)
	
	vagrant up swarmmanager
	vagrant up swarmagent1
	vagrant up swarmagent2
	
	Install SWARM container on the manager node:
	docker run swarm –help
	
	Start Consul:
	*Consul is a modern datacenter runtime that provides service discovery, 
	configuration, and orchestration capabilities.
	  docker run -d -p 8500:8500 --name=consul progrium/consul -server –bootstrap
	
	Start manage node on swarmmanager:(master)
	*The --advertise-addr flag configures the manager node to publish its ip address 
	as the other nodes in the swarm must be able to access the manager at the IP address.
	  docker run -d -p 4000:4000 swarm manage -H :4000 --advertise 192.168.0.248:4000 consul://192.168.0.248:8500
	
	Run swarm join on the swarmagent1 (.246):
	  docker run -d swarm join --advertise=192.168.0.246:2375 consul://192.168.0.248:8500
	
	Run swarm join on the swarmagent2 (.247):
	  docker run -d swarm join --advertise=192.168.0.247:2375 consul://192.168.0.248:8500
	
	Check cluster status:
	  docker -H :4000 info
	
	Run on a container on your swarm cluster:
	  docker -H :4000 run -p 3000:3000 -d container/app
	
	List containers:
	  docker -H :4000 ps
	
	Connect to the container/app:
	  curl 192.168.0.247:3000

<br/>
<br/>

<b>NOTES: Create Docker Host on AWS:</b>

	Aws user/password, etc:    ls -ahl ~/.aws/config
	docker-machine create --driver amazonec2 --amazonec2-region=eu-west-1 --amazonec2-vpc-id=vpc53810a36 --amazonec2-subnet-a8b83af1 --amazonec2-zone c aws02 (installs docker engine, certs, etc)
	docker-machine env aws02
	eval $(docker-machine env aws02)  --will setup env variables
	docker run –d –p 3000:3000 container/app
	docker ps  (see container running)
	docker-machine ip aws02   (determine IP address being used on Amazon)
		output: 52.16.112.236
		curl 52.16.112.236
			ouput: hello World
		* make sure port 3000 is open on the network
		Docker logs
   
   
   
