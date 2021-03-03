# Gcp-Ansible-jar-Demo
JAR deployments in GCE using Ansible
## 1. Prerequisites
  - nginx [version]
  - JAR [addressIp, port, ...]
  - openJDK [version 11]
  - Mysql or MariaDB [version, username, password, port, ....]

## 2. Configuration and preparations


### I - Google Cloud Platform GCP related
first thing make sure that have Google Cloud Platform account
see [google cloud] (http://cloud.google.com)
and fallow this guides to set up you environment for deployment your web application.

1- Creat a new Google Cloud Platform Project :

(https://cloud.google.com/resource-manager/docs/creating-managing-projects).

2- Creat a new service account and obtain a JSON formatted private key for the account, see:

(https://cloud.google.com/iam/docs/creating-managing-service-account-keys)

3- to set up SSH keys to access GCE instances, simply use the following command:

**SSH keys** used to establish a secure connection between two machine where you generate two type of key private/public key you send the public key to the other part and store the private in you machine.
However, to manage all the remote servers requires either 
a very good memory to remember connection details like 
username, remote, address, port,.... or a good way to 
document all the details for each server,  
in this section we get to present a good practise to generate and store your ssh key.
- Creating an SSH Key Pair for User Authentication
```shell
  # ssh-keygen
```
- SSH config file should be your helping hand to control and simplify ssh connections.
first we need to creat a config file :
```shell
 # nano ~/.ssh/config
```
- Example of complete configuration: bas we see blow each configuration in your config file is initialed by the keyword **host** followed by the an idenfifier
```shell
Host auditNord  
  HostName 35.102.10.120
  User apli 
  Port 2222
  IdentityFile ~/.ssh/known_hosts
```
- now we canuse the defined Host identifier for any connection to remote server. for more detail about the configuration visit the following website (https://www.digitalocean.com/community/tutorials/how-to-configure-custom-connection-options-for-your-ssh-client#general-tweaks-and-connection-items)
```shell
#ssh auditNord
```
4- Creating a Virtual Machine with Terraform
After installing terraform and configuring google cloud account. We have to run application using terraform, let's go.
There are many arguments in terraform, but this case we just wanna run application for first steps.
 terraform commands

 ```shell   
 # terraform init 
 This command sets up the environment.
 # terraform plan 
 This command reports configuration will be applied.
 # terraform apply 
 auto-approve This command applies configuration defined on terraform files approving automatically changes.
 # terraform destroy  
 auto-approve Against of command above, this remove everything created
 ``` 
 ```terrafor
provider "google" {
project = "{{YOUR GCP PROJECT}}"
region  = "us-central1"
zone    = "us-central1-c"
}
 ```
__Project:__ field should be your personal project id. The project indicates the default GCP project all of your resources will be created in. Most Terraform resources will have a project field.

__Region:__ and zone are locations for your resources to be created in. The region will be used to choose the default location for regional resources. Regional resources are spread across several zones.

__Zone:__ will be used to choose the default location for zonal resources. Zonal resources exist in a single zone. All zones are a part of a region.

for more detail visit the folowing website 

(https://blog.avenuecode.com/how-to-use-terraform-to-create-a-virtual-machine-in-google-cloud-platform).
(https://registry.terraform.io/providers/hashicorp/google/latest/docs/guides/getting_started)