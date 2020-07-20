---
layout: post
title:  "Adding the license key of IBM i logical partitions managed by Novalink"
date:   2019-10-11 11:04:19
categories: cloud
permalink: /archivers/2019_10_11_add_lic_key_of_ibmi_managed_by_novalink
---

# Dependent PTFs
7.4 MF99301 SI70544
7.3 MF99207 SI69686
7.2 SI71091

# Add the license key whose length has to be 101-bytes of IBM® i logical partitions.
You could add the license key of IBM® i logical partitions by either of the following ways:
1)	Run the below command on Novalink partitions
```
/usr/bin/chlickey -p <system name> -o a --lickey "<license key>"
```

The explanation of the options are as follows:
-p <system name> indicates the logical partition name. You can run “pvmctl vm list” to query the logical parititon name.
-o indicates the type of the operation to be performed. The only supported operation is a. a indicates adding the license information to the license repository.
--lickey <license key> specifies the license key to be added. The length of the license key has to be 101-bytes.

2) Add the license key of IBM® i logical partitions by calling the PowerVC API

API type: POST
API endpoint: /v2.1/{tenant_id}/servers/{server_id}/action
API description: Request to inject an license key of an IBM i virtual machine. Specify the licenseKey action in the request body

Example
```
POST /v2.1/1e51f46700a545f0952170149e73995c/servers/d41752b5-9c38-419f-bf29-8ef335c5e88c/action
X-Auth-Token:a6ddf6f185224091bf72af3590bd06a8
{
       "IBMiServerAddLicense":
       {
          "licenseKey": "1191028013241RCHASC015770SS1V7R4M05050 XXXXXXX9990001001221224        XXXXXXXXXXXXXXXXXX1191028013241"
       }
}
```
