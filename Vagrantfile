VAGRANTFILE_API_VERSION="2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box="sincerely/trusty64"
  config.vm.synced_folder "./", "/vagrant", id: "vagrant-root"

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.options = ['--verbose']
    puppet.manifest_file = "pseudo-cluster.pp"
  end

  config.vm.provision :shell, :path => "provision.sh"

  config.vm.provision "shell", inline: "source /etc/environment"

  config.vm.provision "shell", inline: "cp -f /vagrant/conf/core-site.xml /home/vagrant/hadoop-2.7.0/etc/hadoop/core-site.xml"

  config.vm.provision "shell", inline: "cp -f /vagrant/conf/hdfs-site.xml /home/vagrant/hadoop-2.7.0/etc/hadoop/hdfs-site.xml"
  
end