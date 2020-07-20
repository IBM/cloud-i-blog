---
layout: post
title:  "How to do offline install of cloud-init onto IBM i"
date:   2019-10-15 10:45:33
categories: cloud
permalink: /archivers/2019_10_15_offline_install_of_cloudinit_onto_ibmi
---

The document is only to introduce how to install cloud-init rpm packages offline. 

# Setup rpm running environment
• Download bootstrap.sh and bootstrap.tar.Z to your PC
• Transfer these two files to the /tmp directory on your IBM i system (via FTP, mapped network drive, scp, sftp etc). Make sure to transfer them in binary.
• From a 5250 terminal run the following.
```
QSH CMD('touch -C 819 /tmp/bootstrap.log; /QOpenSys/usr/bin/ksh /tmp/bootstrap.sh > /tmp/bootstrap.log 2>&1')
```
• If you see message QSH005: "Command ended normally with exit status 0" in the job log you're all good. If not, consult /tmp/bootstrap.log.

# Install cloud-init packages
• Refer to https://supportcontent.ibm.com/support/pages/cloud-init-support-ibm-i find the required rpm packages of cloud-init, for example
  - python2-ibm_db-2.0.5.8
  - python2-six-1.10.0-1
  - python2-2.7.15-1
  - cloud-init-1.2-0
  
• Check which packages are not installed. For example run “/Qopensys/pkgs/bin/rpm -qa|grep python2-ibm_db”. If the output is none, that means the package is not installed. The output in below snapshot means python2 has been installed. But python2-ibm_db, python2-six, cloud-init are not installed.
![check packages](../resources/pic/20201015/cloudinit1.png)

• Download missing rpm packages from https://public.dhe.ibm.com/software/ibmi/products/pase/rpms/repo/ to your PC. (Note, different rpm packages may be in different sub-directories, for example, python2-ibm_db and cloud-init locate at ppc64, python2-six locates at noarch),  then transfer them to your IBM i.

• Install rpm packages
```
  > ls /tmp/*.rpm                                      
    /tmp/cloud-init-1.2-100.ibmi7.2.ppc64.rpm          
    /tmp/python2-ibm_db-2.0.5.12-0.ibmi7.2.ppc64.rpm   
    /tmp/python2-six-1.10.0-2.ibmi7.2.noarch.rpm       
    
  > /qopensys/pkgs/bin/rpm -i /tmp/*.rpm
  
  > /Qopensys/pkgs/bin/rpm -qa|grep cloud-init             
    cloud-init-1.2-100.ppc64                               
    
  > /Qopensys/pkgs/bin/rpm -qa|grep      python2-six       
    python2-six-1.10.0-2.noarch                            
    
  > /Qopensys/pkgs/bin/rpm -qa|grep      python2-ibm_db    
    python2-ibm_db-2.0.5.12-0.ppc64                        
```

