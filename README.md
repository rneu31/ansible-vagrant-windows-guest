# ansible-vagrant-windows-guest
Run ansible playbooks on a Windows target created using Vagrant.

# Steps
Inspiration from https://medium.com/the-sysadmin/managing-windows-machines-with-ansible-60395445069f

Assumed that Vagrant and VirtualBox are already installed. If not,
use the trusty ol' search engine!

1. Place your ansible role in `roles\` (`roles\some-ansible-role-name` in this example).

2. Ensure `main.yml` references the role created in step #2

3. Create Windows box via `vagrant up` in directory next to `Vagrantfile`.

   The Vagrantfile points to: https://app.vagrantup.com/mwrock/boxes/Windows2012R2, created from the code here: https://github.com/mwrock/packer-templates. It is important to trust the source of the Vagrant box.

   This is set up to automatically run `main.yml` which points to your role (`roles\some-ansible-role-name`).

4. Log in to the Vagrant box (the password and username for the Vagrant box are both `vagrant`) and verify
   the results of your ansible!

# Notes
- The Vagrantfile is hardcoded to a specific IP address. This matches the IP address specified in `inventory_file`.
  This was to get around an issue where Ansible was not able to detect that the guest was a Windows OS.
