Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "apt update"
  
  config.vm.define "controle" do |controle|
    controle.vm.box = "shekeriev/debian-12"
    controle.disksize.size = '60GB'
    controle.vm.network "private_network", ip: "172.17.177.100"
    controle.vm.hostname = "controle"
    controle.vm.provision "shell", inline: "apt install  git -y"
    controle.vm.provision "ansible_local" do |al|
      al.playbook = "installdocker.yml"
      al.install_mode = "apt"    
    end
    controle.vm.provider "virtualbox" do |vb|
      vb.name = "controle"
      vb.memory = "4048"
      vb.cpus = 4
  end
end

  config.vm.define "web" do |web|
    web.vm.box = "shekeriev/debian-12"
    web.disksize.size = "30GB"
    web.vm.network "private_network", ip: "172.17.177.101"
    web.vm.hostname = "web"
    web.vm.provider "virtualbox" do |vb|
      vb.name = "web"
      vb.memory = "2048"
      vb.cpus = 2
  end
end

  config.vm.define "db" do |db|
    db.vm.box = "shekeriev/debian-12"
    db.disksize.size = "30GB"
    db.vm.network "private_network", ip: "172.17.177.102"
    db.vm.hostname = "db"
    db.vm.provider "virtualbox" do |vb|
      vb.name = "db"
      vb.memory = "2048"
      vb.cpus = 2
  end
 end
end 
