# -*- mode: ruby -*-
# vi: set ft=ruby :

module OS
    def OS.windows?
        (/cygwin|mswin|mingw|bccwin|wince|emx/ =~ RUBY_PLATFORM) != nil
    end

    def OS.mac?
        (/darwin/ =~ RUBY_PLATFORM) != nil
    end

    def OS.unix?
        !OS.windows?
    end

    def OS.linux?
        OS.unix? and not OS.mac?
    end
end

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.box_check_update = false
    config.vm.hostname = "c-notes-node"
    config.vm.network "private_network", ip: "192.168.33.111"
    config.vm.network "public_network"

    if OS.windows?
      puts "=======Vagrant launched from windows======="
      config.vm.synced_folder "d:/code/", "/home/vagrant/code/", type: "nfs"
    elsif OS.mac?
      puts "=======Vagrant launched from mac======="
    elsif OS.linux?
      puts "=======Vagrant launched from linux======="
    else
      puts "=======Vagrant launched from unknown platform======="
    end

    config.vbguest.auto_update = false
    config.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.memory = "4096"
        vb.cpus = 2
    end
    config.vm.provision "shell", path: "provision.sh"
end
