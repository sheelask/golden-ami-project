# golden-ami-project
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

