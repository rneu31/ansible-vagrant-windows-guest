# ansible-vagrant-windows-guest
Run ansible playbooks on a Windows guest created using Vagrant.

<a target='_blank' rel='nofollow' href='https://app.codesponsor.io/link/SbdHU1DzpxTgupfg3iCwZeiZ/rneu31/ansible-vagrant-windows-guest'>
  <img alt='Sponsor' width='888' height='68' src='https://app.codesponsor.io/embed/SbdHU1DzpxTgupfg3iCwZeiZ/rneu31/ansible-vagrant-windows-guest.svg' />
</a>

# Steps
Inspiration from https://medium.com/the-sysadmin/managing-windows-machines-with-ansible-60395445069f

Assumed that Vagrant and VirtualBox are already installed. If not,
use the trusty ol' search engine!

1. Create Windows box via `vagrant up` in directory next to `Vagrantfile`.
   
The Vagrantfile points to: https://app.vagrantup.com/mwrock/boxes/Windows2012R2, created from the code here: https://github.com/mwrock/packer-templates. It is important to trust the source of the Vagrant box.

2. Write your playbook (edit `windows\playbook.yml`) 

4. `cd windows`

5. Test connection via `ansible windows -i hosts -m win_ping` (http://docs.ansible.com/ansible/latest/win_ping_module.html)

6. If success, run playbook `ansible-playbook -i hosts playbook.yml`

# Notes
The password and username for the Vagrant box are both `vagrant`.
 
