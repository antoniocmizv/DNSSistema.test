# Vagrantfile
Vagrant.configure("2") do |config|
  
  # Configuración para la máquina tierra.sistema.test (servidor maestro DNS)
  config.vm.define "tierra" do |tierra|
    tierra.vm.box = "debian/buster64"
    tierra.vm.hostname = "tierra.sistema.test"
    tierra.vm.network "private_network", ip: "192.168.57.103"
    tierra.vm.provision "shell", inline: <<-SHELL
      # Instalar Bind9 para configurar el DNS maestro
      apt-get update
      apt-get install -y bind9
    SHELL
  end

  # Configuración para la máquina venus.sistema.test (servidor esclavo DNS)
  config.vm.define "venus" do |venus|
    venus.vm.box = "debian/buster64"
    venus.vm.hostname = "venus.sistema.test"
    venus.vm.network "private_network", ip: "192.168.57.102"
    venus.vm.provision "shell", inline: <<-SHELL
      # Instalar Bind9 para configurar el DNS esclavo
      apt-get update
      apt-get install -y bind9
    SHELL
  end
end
