
$ansible_remoting_script = <<SCRIPT
iex ((new-object net.webclient).DownloadString('https://github.com/ansible/ansible/raw/devel/examples/scripts/ConfigureRemotingForAnsible.ps1'))
SCRIPT

Vagrant.configure("2") do |config|
  
  config.vm.box = "mwrock/Windows2012R2"
  config.vm.box_version = "0.6.1"
  config.vm.network "private_network", ip: "192.168.53.194"
  config.vm.provision "shell", inline: $ansible_remoting_script

end

