# Introduction

[Checkmk](https://checkmk.com/) is an open source IT monitoring solution. This example shows how to set up Checkmk server and agent using Vagrant so you can test this on your own machine.

# Prerequisites

- [VirtualBox](https://www.virtualbox.org/) (tested with 6.0.8)
- [Vagrant](https://www.vagrantup.com/) (tested with 2.2.5)

# How to use

`vagrant up`

Pay attention to the password that appears when the server is provisioned.
1. Browse to http://192.168.33.10/mysite, login with cmkadmin and the password. 
2. On the left side scroll down to the 'WATO Configuration' menu. Click 'New host'. 
3. At hostname enter 192.168.33.20.
4. At the bottom of the page, press 'Save & go to Services'.
5. Click 'Fix all missing'.
6. Click '2 changes'.
7. Click 'Activate affected.'
Now the host is monitored by Checkmk.

# Clean up

`vagrant destroy -f`
