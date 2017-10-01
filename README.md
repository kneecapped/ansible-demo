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

  * Lets Create a ssh-key, if you already have one skip to next step

    ```
        [root@centos ansible]# ssh-keygen
        Generating public/private rsa key pair.
        Enter file in which to save the key (/root/.ssh/id_rsa): 
        Created directory '/root/.ssh'.
        Enter passphrase (empty for no passphrase): 
        Enter same passphrase again: 
        Your identification has been saved in /root/.ssh/id_rsa.
        Your public key has been saved in /root/.ssh/id_rsa.pub.
        The key fingerprint is:
        SHA256:1FJp6a4p78fgoS5stKAnrH9afzJfp3fnmLE9TFOsxf4 root@centos
        The key's randomart image is:
        +---[RSA 2048]----+
        |          .o     |
        |         o+      |
        |        oo.    o |
        |       . ..     =|
        |        S.     +.|
        |  . .   o .   .o.|
        |.. +.. o *. . + o|
        |o...*.= =.oo. .OE|
        |o+o+ ooO+... .+o+|
        +----[SHA256]-----+

    ```
  * Add the ssh-key to the target linux host, from the ansible control host
  ```
  ssh-copy-id ansible@<linux-host>
  ```

  * Setup hosts.yml

  In the hosts.yml there will be an IP under the linux hosts, replace that with the linux-host that we added the ansible user too as well as loaded the ssh-key onto.
  ```
    ---
    linux:
    hosts:
      192.168.1.90
  ```
