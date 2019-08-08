# vagrant-icebox

[![Gitter](https://badges.gitter.im/vagrant-icebox/community.svg)](https://gitter.im/vagrant-icebox/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

> A vagrant environment to develop Icebox and VirtualBox VMI

## Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Setup](#setup)
- [Troubleshooting](#troubleshooting)
- [References](#references)
- [Maintainers](#maintainers)
- [Contributing](#contributing)
- [License](#license)

## Overview

Icebox is a debugger and tracer working at the hypervisor-level, via virtual
machine introspection.

As it requires a modified VirtualBox and a complicated setup,
this project aims to lower the entry barrier for curious developers and users.

## Requirements

- `vagrant`
- [`vagrant-libvirt`](https://github.com/vagrant-libvirt/vagrant-libvirt) plugin
  (packaged in Debian/Ubuntu)
- [`vagrant-reload`](https://github.com/aidanns/vagrant-reload) plugin
- `ansible >= 2.2.1.0`

## Setup

Example setup on Debian Buster
~~~
$ sudo apt-get install -y vagrant ruby-dev
$ sudo apt-get install vagrant vagrant-libvirt
$ vagrant plugin install vagrant-reload
~~~

### Vagrantfile

Tune the Vagrantfile configuration to your needs.

### Build the environment

- Run `vagrant up --provider=libvirt` or `vagrant up --provider=virtualbox`
- Once the provisioning via `Ansible` is done, ssh into the box with `vagrant ssh`


## Troubleshooting

### NFS

You need to open your firewall for `NFS`. The following commands should make it work for a `Vagrant` box
to access your host `NFS` server:

~~~
firewall-cmd --permanent --add-service=nfs
firewall-cmd --permanent --add-service=rpc-bind
firewall-cmd --permanent --add-service=mountd
firewall-cmd --reload
~~~

## References

- [Icebox](https://github.com/thalium/icebox): Virtual Machine Introspection, Tracing & Debugging 

## Maintainers

[@Wenzel](https://github.com/Wenzel)

## Contributing

PRs accepted.

Small note: If editing the Readme, please conform to the [standard-readme](https://github.com/RichardLitt/standard-readme) specification.

## License

[GNU General Public License v3.0](https://github.com/Wenzel/pyvmidbg/blob/master/LICENSE)
