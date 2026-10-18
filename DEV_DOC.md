# Development document


## Common Requirements
- You can use any tools you want to set up your host virtual machine as well as the provider used in Vagrant (I used VirtualBox).


## Part 1
### Requirements
- you hace to set up 2 machines.
- Write your first Vagrantfile using the latest stable version of the distribution
of your choice as your operating system (I choose Debian 13: 2026-10-18).
- allow only the bare minimum in terms of resources: 1 CPU and 1024 MB of RAM.

### Steps
#### 1. install vagrant
install vargrant on ~/sgoinfre/ because we can't use sudo apt get and add to PATH.
```
mkdir -p "$HOME/.local/bin"
mkdir -p "$HOME/.local/opt/vagrant"
cd /tmp
wget https://releases.hashicorp.com/vagrant/2.4.9/vagrant_2.4.9_linux_amd64.zip
unzip vagrant_2.4.9_linux_amd64.zip \
  -d "$HOME/.local/opt/vagrant"
ln -s "$HOME/.local/opt/vagrant/vagrant" \
  "$HOME/.local/bin/vagrant"
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```
make sure installing succeeded
```
which vagrant
vagrant --version
```
Virtual Box on CLI should be able to use on 42Tokyo environment.
```
command -v VBoxManage
VBoxManage --version
```
you can try how it works
```
mkdir /tmp/hello-vagrant && cd /tmp/hello-vagrant
vagrant init bento/ubuntu-24.04
vagrant up --provider=virtualbox
```
connext with SSH
```
vagrant ssh
```
clean up
```
exit
vagrant halt
```
Vagrant and VirtualBox may consume a significant amount of disk space. To avoid running out of storage, you can change their default storage locations to a larger disk, such as sgoinfre.
```
echo 'export VAGRANT_HOME="$HOME/sgoinfre/vagrant"' >> ~/.zshrc
source ~/.zshrc
mkdir -p "$HOME/sgoinfre/VirtualBox VMs"
VBoxManage setproperty machinefolder "$HOME/sgoinfre/VirtualBox VMs"
```

#### 2. Write Vagrantfile
- Requrements
	1. Ubuntu 26.04.1 LTS
	2. 1 CPU and 1024 MB of RAM


- Configuration version: 2
- Vagrant Box: `bento/debian-13`
- resources: 1 CPU and 1024 MB of RAM
- SSH configure: default
- provider: virtualbox
- network: "private_network"
