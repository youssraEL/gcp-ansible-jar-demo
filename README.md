# Gcp-Ansible-jar-Demo
JAR deployments in GCE using Ansible
## Prerequisites
  - nginx
  - Mysql or MariaDB
## install required software


## configuration and preparations


### I - Google Cloud Platform GCP related
first thing make sure that have Google Cloud Platform account
see [google cloud] (http://cloud.google.com)
and fallow this guides to set up you environment for deployment your web application.

1- Creat a new Google Cloud Platform Project : (https://cloud.google.com/resource-manager/docs/creating-managing-projects).

2- Creat a new service account and obtain a JSON formatted private key for the account, see (https://cloud.google.com/iam/docs/creating-managing-service-account-keys)

3- to set up SSH keys to access GCE instances, simply use the following command:

SSH keys used to establish a secure connection between two machine where you generate two type of key private/public key you send the public key to the other part and store the private in you machine.
Moreover, to manage all the remote servers requires either 
a very good memory to remember connection details like 
username, remote, address, port,.... or a good way to 
document all the details for each server,  
in this section we get to present a good practise to generate and store your ssh key.


'''bash

'''