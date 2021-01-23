# tftp-box

| License | Versioning | Build |
| ------- | ---------- | ----- |
| [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) | [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) | [![Build status](https://ci.appveyor.com/api/projects/status/yvlq9ocwqqr5dslq/branch/master?svg=true)](https://ci.appveyor.com/project/nikAizuddin/tftp-box/branch/master) |

Developer box for TFTP server/client.


## Getting started

```
$ git clone --recursive https://github.com/extra2000/tftp-box.git
$ cd tftp-box
```


## Creating Vagrant Box

Copy vagrant file from `vagrant/examples/` and then create the vagrant box (you can change to `--provider=libvirt` if you want to use Libvirt provider):
```
$ cp -v vagrant/examples/Vagrantfile.tftp-box.fedora-33.x86_64.example vagrant/Vagrantfile.tftp-box
$ vagrant up --provider=virtualbox
```

Provision the vagrant box which will automatically install tftp with dashboard:
Apply `state.highstate` to initialize development environment. Then apply `tftp` state to build `tftp-hpa` Podman image and deploy:
```
$ vagrant ssh tftp-box -- sudo salt-call state.highstate
$ vagrant ssh tftp-box -- sudo salt-call state.sls tftp
```
