# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "wcapp" , primary: true do |wcapp|
    wcapp.vm.box = "centos-6.5-x86_64"
    #wcapp.vm.box_url ="/Users/edwin/Downloads/centos-6.5-x86_64.box"
    wcapp.vm.box_url = "https://dl.dropboxusercontent.com/s/np39xdpw05wfmv4/centos-6.5-x86_64.box"

    wcapp.vm.hostname = "wcapp.example.com"

    wcapp.vm.synced_folder "."                    , "/vagrant", :mount_options => ["dmode=777","fmode=777"]
    wcapp.vm.synced_folder "/Users/edwin/software", "/software"
    #wcapp.vm.synced_folder "."                    , "/vagrant" , type: "nfs"
    #wcapp.vm.synced_folder "/Users/edwin/software", "/software", type: "nfs"

  
    wcapp.vm.network :private_network, ip: "10.10.10.10"
  
    wcapp.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "3500"]
      vb.customize ["modifyvm", :id, "--name"  , "wcapp"]
    end
  
    wcapp.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml"
    
    wcapp.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "wcapp.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"
  
      puppet.facter = {
        "environment"                     => "development",
        "vm_type"                         => "vagrant",
      }
      
    end
  
  end

  config.vm.define "wcdb" , primary: true do |wcdb|
    wcdb.vm.box = "centos-6.5-x86_64"
    wcdb.vm.box_url = "https://dl.dropboxusercontent.com/s/np39xdpw05wfmv4/centos-6.5-x86_64.box"

    wcdb.vm.hostname = "wcdb.example.com"
    wcdb.vm.network :private_network, ip: "10.10.10.5"

    wcdb.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
    wcdb.vm.synced_folder "/Users/edwin/software", "/software"
    #wcdb.vm.synced_folder ".", "/vagrant", type: "nfs"
    #wcdb.vm.synced_folder "/Users/edwin/software", "/software", type: "nfs"
  
    wcdb.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm"     , :id, "--memory", "2000"]
      vb.customize ["modifyvm"     , :id, "--name"  , "wcdb"]
    end

  
    wcdb.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml"
    
    wcdb.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "wcdb.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"
  
      puppet.facter = {
        "environment" => "development",
        "vm_type"     => "vagrant",
      }
      
    end
  
  end  



end
