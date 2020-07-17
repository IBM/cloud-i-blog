---
layout: post
title:  "Move your IBM i virtual machine into IBM Cloud"
date:   2020-07-01 10:15
categories: ansible
permalink: /archivers/2020_0701_move_your_ibm_i_virtual_machine_into_ibm_cloud
---

by Wang Yun, Zhu Li Jun

Many companies and organizations using IBM i show great interests in moving workloads into public cloud in recent years. IBM Cloud is one of several greatest options that the customers can choose to run IBM i workloads in the public cloud. IBM Cloud provides the capability to securely import images and deploy virtual machines of IBM i on Power systems. 

There are different levels of cloud usage for the customers to run their applications and workloads. One typical way is to move the entire IBM i partition from data center into cloud environment. For many shops, single and integrated IBM i system contains almost everything to run the business or do the development and testing work. In this case, moving the entire partition into public cloud means the applications running the business are enabled in the cloud. 

IBM® PowerVC™ is an advanced virtualization and cloud management offering. Built on OpenStack, it provides simplified virtualization management and cloud deployments for IBM AIX®, IBM i and Linux virtual machines (VMs) running on IBM Power Systems™. Many customers already have the PowerVC environment on prem improving administration productivity. Its fast deployment, easy to use, resources controlling and efficient utilization have been well received and proved. This article will introduce how you could move IBM i virtual machines managed by PowerVC into IBM cloud. For more information of how IBM i is supported by PowerVC, please visit the link here: https://www.ibm.com/support/pages/ibm-power-virtualization-center-powervc-ibm-i. 

# Capture your IBM i partition which you want to move to IBM Cloud
Capturing an IBM i virtual machine will take the snapshot of the volumes that the operating system is running on. An image representing such snapshot is created after the capturing and it could be used repeatedly to deploy virtual machines. Such image can also be exported or imported so that its associated virtual machines can be moved across various environments. 

In this example, we select one IBM i 7.4 virtual machine to be migrated. In order to ensure all the data are all captured, the ‘cold’ clone is used. This means that the virtual machine needs to be shut down first. 

Once it has been shut down, the state of the virtual machine turns into ‘shutoff’. A wizard will be shown up in the PowerVC GUI after the ‘Capture’ button is clicked for a specific virtual machine. You must provide a name for your new image and choose which volumes to be captured. There are three options to select whether you want to capture boot set volumes only or additional data volumes. The virtual machine selected in this article does not have IASP created, so that only boot set volumes are needed. 
![Capture IBM i virtual machine](../resources/pic/20200701/m1.png)

It takes a short while to complete the capturing. The new image could be found in the ‘Images’ page after the new image has been successfully created. 
![Image created](../resources/pic/20200701/m2.png)

# Export the captured image
After capturing the volumes, the image needs to be exported to a format that can be transferred to other places. There are multiple ways for you to do this. You could use the PowerVC GUI or the command line. In this example, the command line is used because there are more options that could be leveraged to do the export. 
![Image export](../resources/pic/20200701/m3.png)

The goal of this article is to move the image into public cloud. For different customers and data centers, the connectivity speed to the public cloud is different. Thus, the smaller the image is, the shorter time it will take to move the image to the public cloud. The compress option is used here for this purpose. The exported file is a lot smaller after using the compress option. 

The below command is used to export the image from command line of the PowerVC system. 
```
powervc-image export -i GIST_DEMO -p /root/gist_demo.ova -c
```
The -c option tells that the image will be compressed. The -p option specifies the name and path of the OVA file that will be generated. 
![Image export 2](../resources/pic/20200701/m4.png)

After the image is successfully exported, a file named gist_demo.ova.gz has been created. The size of this image package file is 5.79 GB in this example. This is much smaller than the size of the volumes being captured which is 80 GB. 
![Image export 3](../resources/pic/20200701/m5.png)

# Create object storage space in IBM Cloud
In order to deploy the virtual machine, the image file should be stored in IBM Cloud first. IBM Cloud® Object Storage makes it possible to store practically limitless amounts of data, simply and cost effectively. It is commonly used for data archiving and backup; for web and mobile applications; and as scalable, persistent storage for analytics. You could refer to https://www.ibm.com/cloud/object-storage for more information about IBM Cloud Object Storage. 

It assumes that Cloud Object Storage has already been requested and created as a resource in this article. We’ll start with creating a separate bucket in the Cloud Object Storage space. 

In the resource list of IBM Cloud portal, the cloud object storage is chosen under storage category. 
![Resource list in IBM Cloud](../resources/pic/20200701/m6.png)

You could navigate to the buckets list of the storage by clicking the specific cloud object storage space.

A new bucket named gist-demo-ibmi74 will be created to hold the image file. 
![Cloud object storage](../resources/pic/20200701/m7.png)

# Transfer the exported image to object storage space in IBM Cloud
To transfer large files to IBM Cloud Object Storage, the recommended option is to use Aspera transfer. The integrated IBM Aspera® high-speed data transfer option makes it easy to transfer data to and from IBM Cloud Object Storage. It is the stable and secure way to move the large files to IBM Cloud. For detail information about IBM Aspera, please visit this link: https://www.ibm.com/cloud/aspera. 

After your new bucket of object storage has been created, you could start the transferring of the image package file that was just exported. The IBM Cloud portal supports drag and drop capability so that you could directly drag the file on the GUI. The transferring status could be viewed by clicking the ‘Aspera transfers’ link. 
![Aspera in IBM Cloud](../resources/pic/20200701/m8.png)

The service credential should be also created so that later steps could use it to do image import process. 
![Create service credential in IBM Cloud](../resources/pic/20200701/m7.png)

# Import the image 
The next step following the image transferring is to import the image. Starting from this step, the operations should be done at Power Systems Virtual Server service page. You need to go to ‘Boot images’ page to view and import images. Several items of information should be prepared in order to successfully complete the import. Cloud storage details such as region, image file name, bucket name and access credentials need to be provided. These can all be found via the IBM Cloud Object Storage page. 
![Import image in IBM Cloud](../resources/pic/20200701/m9.png)

For the credential information, you need to click on the ‘Service credentials’ link and select the key name that was just created. Detail information about the credential could be found after clicking and expanding the key on the GUI. ‘access_key_id’ and ‘secret_access_key’ fields should be used for ‘Cloud storage access key’ and ‘Cloud storage secret key’ option when doing the image importing. 
![Retrieve the credential in IBM Cloud](../resources/pic/20200701/m10.png)

# Deploy the virtual machine into IBM Cloud
Once the image has been imported, IBM i virtual machine could be deployed from this image. On the page of ‘Virtual server instances’ of ‘Power System Virtual Server’, you need to click on the button of ‘Create instance’ to deploy the IBM i virtual machines from the image that we just imported. 

The virtual server instance creation page allows you to select operating system type as IBM i, and choose the image from the drop down list which contains the image that was just imported. You could also specify other options to configure the network and other resources. 
![Create virtual machine in IBM Cloud](../resources/pic/20200701/m11.png)

After clicking the ‘create instance’ button, the virtual machine will be created. You could access the system deployed by the web console. The workload and applications are exactly the same as what they were on prem. 
![Create virtual machine complete](../resources/pic/20200701/m12.png)

# Summary
Moving IBM i workloads from data center to IBM Cloud is proved to be possible. If you’ve already had PowerVC environment, the virtual machines being managed by it can be migrated into IBM Cloud much easier. IBM Cloud provides different capabilities that you could take advantage of, and it is secured and productive cloud choice. 
