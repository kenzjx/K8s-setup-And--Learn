
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.define "master" do | w |
  w.vm.hostname = "master"
  w.vm.network "private_network", ip: "192.168.10.100"
  w.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
    vb.name = "master"
  end
  w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
  end
  w.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y git wget vim curl
   SHELL
  end

  config.vm.box = "ubuntu/bionic64"
  config.vm.define "worker-1" do | w |
      w.vm.hostname = "worker-1"
      w.vm.network "private_network", ip: "192.168.10.101"

      w.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
        vb.name = "worker-1"
      end
      w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
    end
   w.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y git wget vim 
   SHELL
  end 
  config.vm.box = "ubuntu/bionic64"
  config.vm.define "worker-2" do | w |
      w.vm.hostname = "worker-2"
      w.vm.network "private_network", ip: "192.168.10.102"

      w.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
        vb.name = "worker-2"
      end
        w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
  end
   w.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y git wget vim curl
   SHELL
  end  
end
