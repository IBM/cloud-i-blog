---
layout: post
title:  "How to use cloud-init on IBM i"
date:   2019-10-08 08:27:10
categories: cloud
permalink: /archivers/2019_10_08_how_to_use_cloudinit_on_ibmi
---

This article explains how to use cloud-init on IBM i.

# Networking setup
Cloud-init helps you to do the networking setup, including:
• Create line descriptions (CLOUDINIT0, CLOUDINIT1 etc.) on Ethernet Port.
• Add TCP interface on each line description and assign the user specified IP to them.
• Add the TCP/IP default routes to the specified gateway.
• Configure the TCP/IP Host Table by adding the entry with specified IP.
• Set up the TCP/IP Domain information with configuring the domain name, domain search list, and domain name servers.

# CL/shell commands running
You can write either CL/shell commands or shell scripts containing these commands, and cloud-init will run them when configuring the VM in the initiation stage. There are several ways to do it:
• You can put the shell commands into the PowerVC “Activation Input” or attach the shell script there (shown below) when doing the VM deployment, the shell script should start with “#!/bin/sh”, Then it can be recognized as shell script.
If you want to run CL commands, you can make it into shell command by inserting it into “system” command. E.g. system "crtlib (test)"

• You can put the CL/shell commands into the cloud-init config(/QOpenSys/pkgs/lib/cloudinit/icfg/cloud.cfg)  “runcmd” section. Below is an example of the “runcmd” section:

• You can also put the shell scripts under the cloud-init scripts folder(/QOpenSys/pkgs/lib/cloudinit/cloud/scripts), and they will be executed in different frequencies, respectively from high to low.
  - per-instance: scripts are run only once on a same VM.
  - per-once: scripts are run only once along the VM deriving life. In other words, if the VM gets re-capture and re-deploy several times, the scripts will be only run in the first time for only one time.
  
# User profile/group profile setup
• USER PROFILE SETUP
Client can specify user profiles with different attributes in cloud-init config file, and cloud-init will create these user accounts with specified attributes when initializing the VM if the account is not there. This configure file should follow the YAML formatting.
  - You need to add default user in the users section if you want the default user to be created by cloud-init.
  - name: the name of user account
  - home/homedir: home directory of the user account. Unless no_create_home is specifically set to True, the home directory will always be created if it is not existing.
  - lock_passwd: whether you want to disable the password for user.
  - gecos: the description of the user account.
  - primary-group: the group profile of the user. Unless no_user_group is specifically set to True, the group profile will be created. Otherwise the user creation will be failed if primary-group account is not there.
  - groups: the supplemental groups of the user. There could be several groups specified with “,” separating them. Unless no_user_group is specifically set to True, the group profile will be created. Otherwise the user creation will be failed if any of groups is not there.
  - expiredate: the expiration date of the user.
  - passwd: the password of the user. 
  - inactive: set the user account inactive or not
  - ssh_authorized_keys: the ssh key specified here will be added into user home directory ~/.ssh/authorized_keys. This will enable the login without password.

• GROUP PROFILE SETUP
Client can specify group profiles with group name and included user profiles in the config file. If group is not existing, by default it will be created with disabling the status and enabling the password.

• DEFAULT_USER
This is the cloud-init default user. If any SSH authorized key is inserted from PowerVC, it will be inserted under the default user’s home directory.

# SSH key manipulation
Client can generate their SSH key pairs and add them into the cloud-init config file, then cloud-init will help insert these key pairs into the target VM’s SSH server. 
• ssh_deletekeys: this is True by default. Cloud-init will delete any existing SSH server keys if ssh_deletekeys=True.
• ssh_keys: add SSH key pair into the ssh_keys section of cloud-init config file, and cloud-init will insert them into the target VM’s SSH server. If ssh_keys is not specified, all key pairs will be generated automatically by cloud-init for target VM’s SSH server.

DO NOT forget the “|” at the end of xxx_private key which will guarantee the format of the key file.

# SSH key injection by PowerVC
Client can select a key pair to inject SSH credentials during virtual machine deployment on PowerVC. The feature has been supported since PowerVC 1.3.2.
