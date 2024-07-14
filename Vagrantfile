

Vagrant.configure("2") do |config|
  # Configuración para la primera máquina virtual
  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/jammy64"
    web1.vm.hostname = "sever1"
    web1.vm.provider "virtualbox" do |vd|
        vd.memory = "512"
        vd.cpus = 1
    end
    web1.vm.network "private_network", ip: "192.168.56.10"
    web1.vm.provision "file", source: "./index.html", destination: "/tmp/index.html"

    # Aprovisionamiento de software 
    web1.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      mv /tmp/index.html /var/www/html/index.html
    SHELL
  end

  # Configuración para la segunda máquina virtual
  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/jammy64"
    web2.vm.hostname = "sever2"
    web2.vm.provider "virtualbox" do |vd|
        vd.memory = "512"
        vd.cpus = 1
    end
    web2.vm.network "private_network", ip: "192.168.56.11"
    web2.vm.provision "file", source: "./index.html", destination: "/tmp/index.html"
    
    # Aprovisionamiento de software 
    web2.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      mv /tmp/index.html /var/www/html/index.html
    SHELL

 
  end
end
