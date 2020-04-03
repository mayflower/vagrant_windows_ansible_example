# Vagrant Windows Ansible Example

An example on how to use Ansible to provision Windows, based on Vagrant

## Requirements

* [VirtualBox](https://www.virtualbox.org/)
* [vagrant](https://www.vagrantup.com/)
* [packer](https://github.com/joefitzgerald/packer-windows/)
* [Windows Templates for Packer](https://github.com/joefitzgerald/packer-windows/)

## Steps

* Create a Window 10 base box with packer.
* `vagrant box add win10 windows_10_virtualbox.box`
* `vagrant init win10`
* `vagrant up`

## Provisioning

The Vagrantfile is configured to uses `shell` provisioning, with powershell and ansible.

The box is be setup with [Chocolatey](https://chocolatey.org/) Package Manager for Windows.

Have a look at the [Ansible Windows modules](https://docs.ansible.com/ansible/latest/modules/list_of_windows_modules.html)
You might also want to take a look at [Ansible's Windows Guides](https://docs.ansible.com/ansible/latest/user_guide/windows.html)

## Connect to the Box

### SSH

* `vagrant ssh`

This is a Cygwin environment

You will find the `C`-Drive in `/cygdrive/c`

### WinRM

You can also connect via WinRM to the box an execute commands, like:

* `vagrant winrm -s powershell -c 'autologon vagrant WORKGROUP vagrant'`
* `vagrant winrm -s powershell -c 'c:/vagrant/PsTools/psexec -i 1 -d -s notepad.exe'`
    * -i 1 = Windows Desktop
    * -d detach -- don't wait for notepad termination
    * -s Run in System Account -- without this, the notepad window is black

### RDP

RDP is enabled.

