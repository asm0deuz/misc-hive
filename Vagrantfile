# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "centos/stream8"
  config.vm.box_version = "20210210.0"


  config.vm.define "ceph-1" do |vm|
    vm.vm.hostname = "ceph-1"
    vm.vm.provider :libvirt do |lv|
      lv.cpu_mode = 'host-passthrough'
      lv.volume_cache = 'none'
      lv.graphics_type = 'none'
      lv.cpus = 8
      lv.memory = 16384
      lv.storage :file, :device => "hdd", :size => '20G', :bus => "ide"
    end
  end


  config.vm.define "ceph-2" do |vm|
    vm.vm.hostname = "ceph-2"
    vm.vm.provider :libvirt do |lv|
      lv.cpu_mode = 'host-passthrough'
      lv.volume_cache = 'none'
      lv.graphics_type = 'none'
      lv.cpus = 8
      lv.memory = 16384
      lv.storage :file, :device => "hdd", :size => '20G', :bus => "ide"
      dl = ('a'..'z').to_a
      (0..2).each do |d|
        lv.storage :file, :device => "hd#{dl[d]}", :size => '20G', :bus => "ide"
      end
    end
  end

  config.vm.synced_folder "/home/teo/sources/", "/vagrant", type: "nfs"

end
