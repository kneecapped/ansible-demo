# Demo Playbook

```
[ansible@centos ansible-demo]$ ansible --version
ansible 2.3.2.0
  config file = /etc/ansible/ansible.cfg
  configured module search path = Default w/o overrides
  python version = 2.7.5 (default, Aug  4 2017, 00:39:18) [GCC 4.8.5 20150623 (Red Hat 4.8.5-16)]

[ansible@centos ansible-demo]$ uname -a
Linux centos 3.10.0-693.2.2.el7.x86_64 #1 SMP Tue Sep 12 22:26:13 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

[ansible@centos ansible-demo]$ python --version
Python 2.7.5
```
## Pre-reqs
  * ansible
  * python 2.7.*

### Setup
  * Setup ssh keys and users on target linux hosts.

   On the target linux hosts lets create a user called `ansible`  
   Assuming you have a root user.
   ```
   ssh root@<linux-host>
   adduser ansible
   passwd ansible  # Enter and confirm password
   ```
   Now on your ansible control node, or server/box we want to setup a ssh key, because we don't want to have to use passwords when running our ansible-playbook.  
   On the machine on which you will be running the ansible-playbook
    1. Lets Create a ssh-key, if you already have one skip to next step
    ```
    ssh-keygen # Just press enter.., or 
    ```
    2. Add the ssh-key to the target linux host
