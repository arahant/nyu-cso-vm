# nyu-cso-vm

There is a `Vagrantfile` which creates an instance of `Ubuntu 20.04` distribution, along with the necessary packages to run your C programs.

## Installing dependencies

You need to install **Virtualbox** and **Vagrant** on your systems.

### Windows

1. Download Virtualbox manually: [Virtualbox downloads](https://www.virtualbox.org/wiki/Downloads)
1. Download Vagrant manually: [Vagrant downloads](https://www.vagrantup.com/downloads.html)
1. Additional configuration (part 1)
    - Vagrant requires an `ssh client` which Windows doesn't have by default. The easiest way to solve this is to install git with the optional unix tools from: http://git-scm.com/downloads
    - Here is a great tutorial: http://tech.osteel.me/posts/2015/01/25/how-to-use-vagrant-on-windows.html
1. Additional configuration (part 2)
    - VirtualBox requires that Hardware-Assisted Virtualization is enabled in order to work in 64-bit mode. But, some PC laptop manufacturers disable this by default. ` ̄\_(ツ)_/ ̄`
    - If when you try and bring vagrant up you get an error that it cannot load the 64-bit VM then you need to change your BIOS settings to enable VT-x/VT-d.
    - If you don't know how to do this, you need to consult with your PC
    documentation because this is different for every manufacturer.   (... or just buy a Mac ;) )


### Unix (Mac)

1. `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"` to install homebrew
1. `brew install git` to install git (only if you don't have it)
1. `brew cask install virtualbox` to install virtualbox
1. `brew cask install vagrant` to install vagrant

### Linux

1. `git` is pre-installed on Linux distributions
1. `sudo apt-get install virtualbox` to install virtualbox
1. `sudo apt-get install vagrant` to install vagrant

## Vagrant

[More documentation on Vagrant](https://www.vagrantup.com/docs)

### Setting up the VM through Vagrant
1. `git clone https://github.com/arahant/nyu-cso-vm.git`
1. `cd nyu-cso-vm`
1. `vagrant up --provision`
1. `vagrant ssh`
1. `cd /vagrant`
1. `ls`

### Logging in into your Vagrant VM

1. `vagrant up --provision`
1. `vagrant ssh`
1. `cd /vagrant`

### Logging out of your Vagrant VM

1. `exit` - should exit the VM and bring you back to your local system
1. `vagrant halt` should stop the VM (remember to stop your VMs every time you're done using the VM or it will keep running in the background)

### Destroying your VM after the term completes

1. Remember to destroy your VM after your term completes.
    - `vagrant destroy` will NOT delete your files, just the VM on your system.

## Copying your code from your Linux (VM) to Linserv1

You can login into your VM as instructed before. Then, follow the commands below to transfer from your VM/local system to `linserv1`

1. `ssh username@access.cims.nyu.edu`, where `username` is your **netid**. Type your password when you're prompted, and voila!

1. `pwd` to complete path to your current dir.

1. `ssh linserv1`. Now you are on a third Unix machine (`linserv1`).

1. You use `scp` (secure copy) to copy files from one Unix machine to another.
    - `scp -r /full/path/to/folder abc123@access.cims.nyu.edu:/home/abc123` copies `folder` and everything in it on your local system to `/home/abc123` on linserv1
    - `scp /full/path/to/folder/file.py abc123@access.cims.nyu.edu:/home/abc123/folder` copies `file.py` in `folder` on your local system to `/home/abc123/folder` on linserv1
