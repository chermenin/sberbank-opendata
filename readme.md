## Sberbank Open Data Dashboard

### 1. Dashboard preview

![Dashboard preview](/images/dashboard.png)


### 2. Requirements and data

The data were downloaded from http://www.sberbank.com/ru/opendata. [Ansible](https://www.ansible.com/) and [Vagrant](https://www.vagrantup.com/) are required for deploying this demo. At the moment only [VirtualBox](https://www.virtualbox.org/) is supported as a provider for Vagrant.


### 3. Deploy and test
To deploy and test this demo you have to clone the project and execute following command in the project directory:

> vagrant up

When a provisioning process will be finished you can open the dashboard using this link: http://localhost:5601/app/kibana#/dashboard/73ff3550-8dbd-11e7-aead-2f95a60451cd
