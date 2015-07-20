# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 80, host: 8080 # must match the port used for callback

  config.vm.provision :shell, inline: "sed -i 's/^mesg n$/tty -s \&\& mesg n/g' /root/.profile", privileged: true
  config.vm.provision :shell, path: 'docker-compose.sh', privileged: false
  config.vm.provision :shell, inline: 'cd /vagrant && sg docker "docker-compose up"', privileged: false
  #config.vm.provision :shell, inline: 'cd /vagrant && bash deploy.sh'
end
