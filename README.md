# Ansbile-role-for-custom-AWS-vpc-subnets-natgateway
Ansible Role for  creating AWS custom VPC, Subnets, Nat gateway, App and DB instances 

======

This Repository is for creating AWS custom VPC with public and private subnets and launching an NAT gatway in the public subnet to provide internet access to the private subnet instances by using Ansible role called vpc.

Creating a VPC , CIDR: 10.22.0.0/16
Creating a Public subnet , CIDR: 10.22.0.0/24
Creating a Public subnet with security groups, Internet gateway ,Route table, NAT gateway
Launching an Ec2 instance for Appication server
Creating a Private subnet with Routetable and associate with NAT gateway , CIDR: 10.22.1.0/24

ansibe role  execution

ansible-playbook vpc.yml --extra-vars "vpc_name=custom-vpc"

======

Note: once the APP and DB instances were launched

ssh to APP instance and then , SSH to DB instance by using your .pem key. once you logged in to the DB instance , check whether its accessing the internet

ssh ec2-user@DB-server -i yourkey.pem

once this step is done , then try to execute the below steps to enable the passowrdless authentication between APP and DB servers by generating SSH keys between the two servers by using the below steps

App-server
ssh-keygen -t rsa, ssh-copy-id ec2-user@db-server-IP, ssh-copy-id ec2-user@APP-server-IP

DB-server
ssh-keygen -t rsa, ssh-copy-id ec2-user@db-server-IP, ssh-copy-id ec2-user@APP-server-IP
