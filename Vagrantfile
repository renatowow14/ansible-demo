Vagrant.configure("2") do |config|

    config.vm.define "wordpress" do |wordpress|
    wordpress.vm.hostname = "wordpress"
    wordpress.vm.box = "debian/buster64"
    wordpress.vm.network "private_network", ip: "172.17.177.40", virtualbox__intnet: true
    wordpress.vm.network "forwarded_port", guest: 80, host: 80
    wordpress.vbguest.auto_update = true
  
    wordpress.vm.provision "shell", inline: <<-SHELL
        set -euxo pipefail
        # Configure ssh vagrant
        mkdir -p /home/vagrant/.ssh/
        apt-get install -y openssh-server
        sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config
        chown -R vagrant:vagrant /home/vagrant/.ssh
        echo "StrictHostKeyChecking no" > /home/vagrant/.ssh/config
        chown -R vagrant:vagrant /home/vagrant/.ssh
        sudo chown 1000:1000 /home/vagrant/.ssh
        echo "root:aluno" | chpasswd
        /etc/init.d/ssh restart
    SHELL
    end 
    config.vm.define "mysql" do |mysql|
    mysql.vm.hostname = "mysql"
    mysql.vm.box = "debian/buster64"
    mysql.vm.network "private_network", ip: "172.17.177.41", virtualbox__intnet: true
    mysql.vbguest.auto_update = true
  
    config.vm.provision "shell", inline: <<-SHELL
        set -euxo pipefail
        # Configure ssh vagrant
        mkdir -p /home/vagrant/.ssh/
        apt-get install -y openssh-server
        sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config
        chown -R vagrant:vagrant /home/vagrant/.ssh
        echo "StrictHostKeyChecking no" > /home/vagrant/.ssh/config
        chown -R vagrant:vagrant /home/vagrant/.ssh
        sudo chown 1000:1000 /home/vagrant/.ssh
        echo "root:aluno" | chpasswd
        /etc/init.d/ssh restart
    SHELL
    end
  end
  