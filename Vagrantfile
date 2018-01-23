$ansible_remoting_script = <<SCRIPT
iex ((new-object net.webclient).DownloadString('https://github.com/ansible/ansible/raw/devel/examples/scripts/ConfigureRemotingForAnsible.ps1'))
SCRIPT

$update_ps = <<SCRIPT
Invoke-WebRequest http://download.microsoft.com/download/2/C/6/2C6E1B4A-EBE5-48A6-B225-2D2058A9CEFB/Win8.1AndW2K12R2-KB3134758-x64.msu -OutFile C:\\Win8.1AndW2K12R2-KB3134758-x64.msu

& wusa.exe C:\\Win8.1AndW2K12R2-KB3134758-x64.msu /extract:C:\\tmp\\

& dism.exe /online /add-package /PackagePath:C:\\tmp\\WindowsBlue-KB3134758-x64.cab /norestart

## The above dism command exits with a code 3010 which in windows means
## 'reboot required'. Packer/ansible sees the 3010 as non-0 and fails the build. 
exit 0
SCRIPT

Vagrant.configure("2") do |config|
  
  config.vm.box = "mwrock/Windows2012R2"
  config.vm.box_version = "0.6.1"
  config.vm.network "private_network", ip: "192.168.53.195"
  config.vm.provision "shell", inline: $ansible_remoting_script
  config.vm.provision "shell", inline: $update_ps
  config.vm.communicator == :winrm
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "main.yml"
    ansible.inventory_path = "inventory_file"
    ansible.verbose = "-vvv"
  end

end
