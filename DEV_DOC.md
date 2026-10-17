# Development document

## steps
### 1. install vagrant
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

### 2. Write Vagrantfile
