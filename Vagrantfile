# -*- mode: ruby -*-
# vi: set ft=ruby :

dir = Dir.pwd
vagrant_dir = File.expand_path(File.dirname(__FILE__))

# Vagrantfile API/syntax version.
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Default Ubuntu Box
  #
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu"
  #
  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system. Sources of other Vagrant
  # boxes are provided in this Project's README.
  #
  # 32-bit Ubuntu 13.10 Saucy Salamander
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-i386-vagrant-disk1.box"
  #
  # 64-bit Ubuntu 13.10 Saucy Salamander
  # config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/saucy/current/saucy-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.hostname = "ubuntu"

  # Forward Agent
  #
  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  # VirtualBox-specific configuration, to fine-tune various options.
  #
  config.vm.provider :virtualbox do |vb|
  # Boot with graphical user interface ("GUI")
    vb.gui = true
  #
  # You may have to comment out or tinker with the values of some of the
  # customizations, below, to suit the needs/limits of your local machine
  # For a 32-bit VM
    vb.customize ["modifyvm", :id, "--memory", "1048"]
    vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    vb.customize ["modifyvm", :id, "--vram", "64"]
  #
  # For a 64-bit VM
  # vb.customize ["modifyvm", :id, "--memory", "2048"]
  # vb.customize ["modifyvm", :id, "--cpus", "2"]
  # vb.customize ["modifyvm", :id, "--graphicscontroller", "vboxvga"]
  # vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
  # vb.customize ["modifyvm", :id, "--ioapic", "on"]
  # vb.customize ["modifyvm", :id, "--vram", "128"]
  # vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
  #
  # View the documentation for the provider you're using for more
  # information on available options.
  end
  
  # Provisioning
  #
  # Process one or more provisioning scripts depending on the existence of custom files.
  #
  # provison-pre.sh
  #
  # provison-pre.sh acts as a pre-hook to the default provisioning script. Anything that
  # should run before the shell commands laid out in bootstrap.sh (or your provision-custom.sh
  # file) should go in this script. If it does not exist, no extra provisioning will run.
  if File.exists?(File.join(vagrant_dir,'provision','provision-pre.sh')) then
    config.vm.provision :shell, :path => File.join( "provision", "provision-pre.sh" )
  end
  #
  # bootstrap.sh or provision-custom.sh
  #
  # By default, our Vagrantfile is set to use the bootstrap.sh bash script located in the
  # provision directory. If it is detected that a provision-custom.sh script has been
  # created, it is run as a replacement. This is an opportunity to replace the entirety
  # of the provisioning provided by the default bootstrap.sh.
  if File.exists?(File.join(vagrant_dir,'provision','provision-custom.sh')) then
    config.vm.provision :shell, :path => File.join( "provision", "provision-custom.sh" )
  else
    config.vm.provision :shell, :path => File.join( "provision", "bootstrap.sh" )
  end
  #
  # provision-post.sh
  #
  # provision-post.sh acts as a post-hook to the default provisioning. Anything that should
  # run after the shell commands laid out in bootstrap.sh or provision-custom.sh should be
  # put into this file. This provides a good opportunity to install additional packages
  # without having to replace the entire default provisioning script.
  if File.exists?(File.join(vagrant_dir,'provision','provision-post.sh')) then
    config.vm.provision :shell, :path => File.join( "provision", "provision-post.sh" )
  end
end
