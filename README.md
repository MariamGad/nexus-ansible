# nexus-ansible
## Overview
Install Latest Sonatype Nexus 3 on CentOS 9 using ansible \
[Sonatype Nexus](https://www.sonatype.com/products/nexus-repository) is one of the best open-source artifact management tools. It is some tool that you cannot avoid in your CI/CD pipeline. It effectively manages deployable artifacts.

---

## Prerequisites
* Ansible master node
  * Install python3 `sudo yum install python3`
  * Install git `sudo yum install git`
  * Install ansible `sudo yum install ansible`
  * Set Passwordless authentication between master and hosts (nexus machine) `ssh-keygen` , `ssh-copy-id root@IP_address`
  * Add inventory file 
    ```
    [hosts]
    nexus ansible_host=remote_host_IP
    ```
* Nexus node
  * Minimum 1 VCPU & 2 GB Memory.
  * Install OpenJDK 8.
  
 ---
 
 ## Steps
 * Update the `yum` packages
 * Install  `wget` utility
 * allow firewall ports `22 and 8081`
 * Create a directory named `app`
 * Download the latest nexus in app directory
 * Untar the downloaded file
 * Rename the untared file to `nexus`.
 * Create a service user named `nexus`.
 * Change the ownership of nexus files to `nexus` user
 * Create a nexus systemd unit file `/etc/systemd/system/nexus.service`
 * Start and enable nexus service

---
## Validation 
* Visit `http://localhost:8081`
* Log in using default username `admin ` and password found in `app/sonatype-work/nexus3/admin.password` \
#### Now you will be able to see the nexus homepage 
![image](https://user-images.githubusercontent.com/47721226/231821274-99e21b0c-b012-41a0-8c2c-60ea992717d1.png)
