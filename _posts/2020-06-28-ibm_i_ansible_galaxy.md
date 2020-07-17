---
layout: post
title:  "Introducing Ansible Content for IBM Power Systems - IBM i"
date:   2020-06-28 11:30
categories: ansible
permalink: /archivers/2020_0628_ansible_galaxy_for_ibm_i
---

by Wang Yun

# What is Ansible Galaxy?
Ansible Galaxy is the online website allowing third parties to provide Ansible modules, plug-ins and roles to achieve specific automations, workflows and tasks. For more information about Ansible Galaxy, please visit the link here: https://galaxy.ansible.com/. 

# Ansible Content for IBM Power Systems - IBM i
The Ansible Content for IBM Power Systems - IBM i (IBM i Ansible collections) provides modules, action plugins, roles and sample playbooks to automate tasks on IBM i, such as command execution, system and application configuration, work management, fix management, application deployment, etc. The detail information could be found from the following link:
https://galaxy.ansible.com/ibm/power_ibmi

# Some key information can be found in the page of above link:
1.	Collection installation information – This provides the command of how to install IBM i collections onto Ansible engine server. 
2.	Docs Site – A link is provided to navigate to the documentation website of IBM i collections. The document introduces the steps to enable IBM i as Ansible endpoints, such as installing required software and PTFs, etc. Also, the module usage explanations have been provided.  
3.	Repo – IBM i Ansible collections are open sourced that all the code and playbook scripts can be downloaded from public github repository. For each release of the collections, a corresponding branch is created in the repository. In addition, different development branches are also created in the purpose of integrating fixes and containing non-released functions. Normally, only released versions of IBM i collections can be downloaded via Galaxy. However, the collections under development could be accessed and downloaded from the development branch of github repository directly. 
