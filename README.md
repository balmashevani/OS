## Usage

This playbook will create a nginx rrobin balancing page for two pages (web1 and web2)

## Start

Before the installation we will need a custom CentOS7 virtual box image with SElinux disabled.

### DON`T FORGET TO EDIT VagrantFile with path to your ssh folder

## Installation

Let's start our virtual machines with Vagrant. Make sure you are using the latest version of vagrant (2.2.19)

```
vagrant up
```
Then let's start our playbook

```
ansible-playbook nginx
```

## Post Installation

If have no errors on summary you can proceed to http://192.168.11.113 to see if your balancer works

It should look like this:

<a href="https://ibb.co/kq8VjL5"><img src="https://i.ibb.co/xzjKWnX/vagrant-result.png" alt="vagrant-result" border="0"></a>

Try refreshing the page to see if numbers on page are changing. If they don`t change try using CTRL+F5 to refresh cache as well

Different page:

<a href="https://ibb.co/qWb7P8v"><img src="https://i.ibb.co/9VRcC07/vagrant-sec-page.png" alt="vagrant-sec-page" border="0"></a>

## Done

You can get yourself a coffee! ☕
