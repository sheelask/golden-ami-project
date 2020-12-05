# Golden AMI creation using Packer and Chef
This repository will contain the packer templates required to build and harden an AWS AMI

# Install Packer
For this example I will be following steps required to run the installation and configuration of Packer on a Linux machine
This setup can be done on your local workstation. 

```
wget https://releases.hashicorp.com/packer/1.5.6/packer_1.5.6_linux_amd64.zip -O packer.zip
```

Now unzip the packer executable and copy it to your `$PATH` so that you can run packer commands from anywhere on the cli
```
unzip packer.zip
sudo mv packer /usr/bin/
```

That is all the steps required to setup packer. To test the setup run the following command 

```
packer --help
```

# Installing Packer plugins 

Packer plugins can be installed two ways
1) By simply downloading the plugin binary and placing it in the path
2) Cloning the repository of the plugin, building it locally, and then storing it in the path 

The first method is very straigth-forward similar to how we installed packer. 

To do it using the second method, we would need to install go (version >= 1.11) on our local workstations.

```
# Find the version available 
$ sudo apt list -a golang-go
Listing... Done
golang-go/focal,now 2:1.13~1ubuntu2 amd64

$ sudo apt-get install -y golang-go==2:1.13~1ubuntu2
```

To download the plugin, clone the git repo 

```
git clone https://github.com/SwampDragons/packer-provisioner-comment.git
```

Then move to the new folder 
```
cd packer-provisioner-comment/
```

```
go mod download
```

```
go build
```

Now that the plugin binary has been created, we need to decide how we make the plugin available. We can either copy it to the 
global $PATH for all users, or put it in `~/.packer.d/plugins` path to make it available for your user only. 

```
mkdir ~/.packer.d/plugins
```

Note that plugins must by named in the packer-type-name format — in this case, packer-provisioner-comment

```
mv main ~/.packer.d/plugins/packer-provision-comment
```

