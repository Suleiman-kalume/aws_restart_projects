# Overview

This lab provides the basic overview of Launching, managing, resizing and monitoring of an amazon EC2 instance.

## Amazon Elastic Compute Cloud (Amazon EC2) 
Is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.
Amazon EC2's simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon's proven computing environment. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.

Amazon EC2 changes the economics of computing by allowing you to pay only for capacity that you actually use. Amazon EC2 provides developers the tools to build failure resilient applications and isolate themselves from common failure scenarios.

By the end of this lab, you will be able to:

Launch a web server with termination protection enabled

Monitor Your EC2 instance

Modify the security group that your web server is using to allow HTTP access

Resize your Amazon EC2 instance to scale

Test termination protection

Terminate your EC2 instance

## Task1 Launching your EC2 instance

In this task, you will launch an Amazon EC2 instance with termination protection. Termination protection prevents you from accidentally terminating an EC2 instance. You will deploy your instance with a User Data script that will allow you to deploy a simple web server.

In the AWS Management Console on the Services menu, choose EC2.

In the left navigation pane, choose EC2 Dashboard to ensure that you are on the dashboard page.

Choose Launch instance, and then select Launch instance.

## Step 1: Naming your EC2 instance

When you name your instance, AWS creates a key value pair. The key for this pair is Name, and the value is the name you enter for your EC2 instance.

In the Name and tags pane, in the Name text box, enter Web Server.

## Step 2: Choosing an Amazon Machine Image (AMI)

An AMI provides the information required to launch an instance, which is a virtual server in the cloud. An AMI includes the following:

A template for the root volume for the instance (for example, an operating system or an application server with applications)

Launch permissions that control which AWS accounts can use the AMI to launch instances

A block device mapping that specifies the volumes to attach to the instance when it is launched

The Quick Start list contains the most commonly used AMIs. You can also create your own AMI or select an AMI from the AWS Marketplace, an online store where you can sell or buy software that runs on AWS.

Locate the Application and OS Images (Amazon Machine Image) pane. 

Under AMI Machine Image (AMI), notice that the Amazon Linux 2 AMI image is selected by default. Keep this setting.

## Step 3: Choosing an instance type

Amazon EC2 provides a wide selection of instance types optimized to fit different use cases. Instance types comprise varying combinations of CPU, memory, storage, and networking capacity and give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type includes one or more instance sizes so that you can scale your resources to the requirements of your target workload.

Select a t3.micro instance. This instance type has 2 virtual CPU and 1 GiB of memory.

From the dropdown, select t3.micro.

NOTE: You may be restricted from using other instance types in this lab.

## Step 4: Configuring a key pair

Amazon EC2 uses public–key cryptography to encrypt and decrypt login information. To log in to your instance, you must create a key pair, specify the name of the key pair when you launch the instance, and provide the private key when you connect to the instance.

In this lab, you do not log in to your instance, so you do not require a key pair.

In the Key pair (login) pane, select Proceed without a key pair (Not recommended).

## Step 5: Configuring the network settings
 
You use this pane to configure networking settings.

The VPC indicates which virtual private cloud (VPC) you want to launch the instance into. You can have multiple VPCs, including different ones for development, testing, and production.

In the Network settings pane, choose Edit

For VPC - required, select Lab VPC.

Still in the Network settings pane, configure the Security Group as follows:

Security group name - required: Web Server security group

Description: Security group for my web server

A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you associate one or more security groups with the instance. You add rules to each security group that allow traffic to or from its associated instances. You can modify the rules for a security group at any time; the new rules are automatically applied to all instances that are associated with the security group.

Under Inbound security groups rules select the Remove

In this lab, you will not log into your instance using SSH. Removing SSH access will improve the security of the instance.

## Step 6: Adding storage

Amazon EC2 stores data on a network-attached virtual disk called Amazon Elastic Block Store (Amazon EBS).

You launch the EC2 instance using a default 8 GiB disk volume. This is your root volume (also known as a boot volume).

In the Configure storage pane, keep the default storage configuration.

## Step 7: Configuring advanced details

Expand the Advanced details pane.

Select the dropdown for Termination protection, then choose Enable.

When you launch an instance in Amazon EC2, you have the option of passing user data to the instance. These commands can be used to perform common automated configuration tasks and even run scripts after the instance starts. 
