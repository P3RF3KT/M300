Vagrant.configure("2") do |config|
config.vm.define "master" do |subconfig|
  subconfig.vm.box = "bento/ubuntu-16.04"
  subconfig.vm.hostname = "master"
  subconfig.vm.network :private_network, ip: "10.0.0.10"
  subconfig.vm.synced_folder ".", "/var/www/html"
config.vm.provision "shell", inline: <<-SHELL
  sudo apt-get update -y
  sudo apt-get install -y apache2 
  cd /var/www/html/
  sudo a2enmod proxy
  sudo a2enmod proxy_http
  sudo a2enmod proxy_balancer
  sudo a2enmod lbmethod_byrequests
  sudo systemctl restart apache2
  sudo apt -y install ufw
  sudo ufw enable
  sudo ufw allow 80/tcp
  sudo ufw allow 8080/tcp
SHELL
end
  
config.vm.define "node1" do |subconfig|
  subconfig.vm.box = "bento/ubuntu-16.04"
  subconfig.vm.hostname = "node1"
  subconfig.vm.network :private_network, ip: "10.0.0.11"
config.vm.provision "shell", inline: <<-SHELL
  sudo apt-get update -y
SHELL
end
	
  config.vm.define "node3" do |subconfig|
    subconfig.vm.box = "hashicorp/precise64"
	subconfig.vm.hostname = "node3"
	subconfig.vm.network :private_network, ip: "10.0.0.12"
    end
	
  config.vm.provision "shell", inline: <<-SHELL
    apt-get install -y avahi-daemon libnss-mdns
  SHELL
end
