# dev-deployment-scripts

## Overview
I use this repository to quickly set up local vm's with the software I want to use for development. This is definitely not intended for prime time, but rather something that as a Windows user I have to do repetitively. It's very basic and simple, but gets me up and running in multiple environments very quickly. New roles for software will continue to be added and updated.

The repository currently includes the following:
- Ubuntu vm with Ansible installed using Vagrant
- MongoDB role
- MySQL role
- NodeJS role
- Pip role
- Supervisord role

I am currently working on adding the following roles:
- Java role

## Instructions
The vm name is currently **dev-machine**. If you want to change the machine name or IP, simply update the *dev.inventory*, *hosts*, and *Vagrantfile* files with your desired machine name and IP. To start the vm, run:

```bash
$ vagrant up dev-machine
```

Once the vm is running, you can ssh into the box as the *vagrant* user with the following command:

```bash
$ vagrant ssh dev-machine
```

I created only one playbook and used tags for flexibility for what you want to install. I did this for two reasons. First, it's the way it works at my job, so it is what I am used to. Second, I do not have specific deployment strategies, such as a web server or application, in mind for this. With that in mind, to run the playbook with a specific role or roles, an example command would look as follows:

```bash
$ cd /vagrant
$ ansible-playbook -i dev.inventory --tags install-mongodb,install-nodejs -c local site.yml 
```

After the playbook completes execution, the software you need should be installed on the vm and you are ready to start working.
