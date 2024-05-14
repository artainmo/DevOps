# Cloud

## Table of contents

## Udemy course - AWS certified cloud practitioner
Other cloud providers than amazon exist. Here, we will specifically learn how to use AWS. However, this knowledge can also be applied to other cloud platforms.

In this course 40 amazon web services (AWS) out of 200+ will be covered. The 'cloud practitioner' certificate is foundational. It can be followed by other certificates, usually the 'solutions architect' which contains more practice, and lastly a specialty certificate such as the 'machine learning' or 'security' AWS certificate.

To use amazon's cloud products we first need to create an AWS account to then access the AWS platform.

### What is cloud computing?
A server is necessary to host a website, contains central processing units (CPU) to compute and random-access memory (RAM) for memory that can be stored and retrieved quickly. A server can also have a database for long-term data storage and routers, switch, DNS server for networking.

In the past own website would run on own server(s). This comes with downsides such as costs related to buying servers, space, power supply, maintenance, infrastructure monitoring, scaling or replacing hardware takes more time and is more complicated.<br>
The cloud resolves those problems by allowing rental of external servers and thus delegation of associated tasks.

Cloud computing is the on-demand delivery of computing power, database storage, applications, and other IT resources.<br>
Via a web-applications you can indicate how much cloud computing resources you need. Usually with cloud platforms you only pay for what you use which we call pay-as-you-go pricing. 

Netflix and dropbox are examples of services who are built on AWS.

Private cloud are cloud services used by a single organization. While public cloud is delivered to the public via internet. AWS, Microsoft Azure and Google cloud are public clouds. Hybrid clouds have some own servers to store sensitive assets while it also uses a public cloud.

Different types of cloud computing exist. Infrastructure as a service (IaaS) provides the hardware only, thus you can install your own OS and other programs on it. Platform as a service (PaaS) also provides the DevOps so the client is only responsible for the data and applications/code. Lastly, software as a service (SaaS) is a complete product that is run and managed by the service provider.<br>
![Screen Shot 2024-05-14 at 11 29 32](https://github.com/artainmo/DevOps/assets/53705599/73284c98-a2b2-4fd0-a10f-4f67f48d50b9)<br>
'Amazon EC2' is an AWS service example of IaaS. 'Elastic Beanstalk' is an AWS service example of PaaS. Heroku is another service that provides PaaS. Many AWS services are SaaS, for example Rekognition for machine-learning provides a pre-trained model.

### AWS cloud overview
In 2002 the cloud at amazon was internally launched. In 2003 they had the idea of sharing with others and in 2004 they launched their cloud publicly.<br>
In 2019 AWS accounted for 47% of the market with microsoft being second at 22%.

AWS enables users to build scalable applications in a diverse set of industries. Its use cases include hosting of websites or mobile apps, gaming, enterprise IT, big data analytics.

At AWS we pay for compute time and amount of stored data. Data transfer out of the AWS cloud is free.

AWS is global.<br>
It has regions all over the world with regions referring to clusters of data centers. Due to legal regions when launching a new application you may need to choose a local region. Else it is best to choose a region close to customers to reduce latency. Available services and pricing can also be variable across regions.<br>
Each region has many availability zones (AZ). Each AZ is one or more separate data center so that if one fails another AZ can be used instead.<br>
AWS has more than 400+ points of presence in 90+ cities across 40+ countries which allows content delivery to end users with lowest latency possible.

The shared responsibility model defines the distribution of responsibilities for security in the AWS cloud. The client is responsible for data and AWS for cloud.

### Identity and Access Management (IAM)
IAM is a global service, meaning it is available in all regions. 

When you create a AWS account you are the root user. However, it is best practice to work via admin users who don't have all permissions.
IAM service allows the creation of users and groups in our AWS account for them to have certain permissions or not on our AWS account. Those permissions can be defined in a JSON document we call a 'policy'. The 'least privilege' principle should be used, it means a user should not receive more permissions than necessary.

![Screen Shot 2024-05-14 at 14 27 17](https://github.com/artainmo/DevOps/assets/53705599/4b425dce-83ae-4c9d-abea-389fb6fdcd61)

To protect your users you can also create password policies which define how strong the users' passwords must be, if users can/must change their password and so on.<br>
For ideal security you can use multi-factor authentication (MFA) which consists of a regular password next to a security device you own. In AWS, MFA devices can be virtual such as Google Authenticator or Authy, else they can be physical such as special security usb keys made by third parties.

In the AWS platform you can create policies and associate them with specific users or groups. Users can be associated with groups and thus policies associated with a group would apply to all the users within that group.

AWS can be accessed via the management console, thus the online platform protected by password and MFA. But also via a command line interface (CLI) which is protected by access keys. Lastly, the software developer kit (SDK) which is used when calling AWS APIs from your application code and is also protected by access keys.<br>
Use link on AWS website to download and install the CLI, after in terminal you can use the 'aws' executable. Start with `aws configure` command for setup.<br>
Alternatively, if you don't want to use own terminal, in AWS platform you can also find a terminal named 'CloudShell'.

IAM Roles are permission policies not for users but instead for AWS services.

IAM Security Tools such as 'IAM Credentials report' can help us view general information and credentials of users and 'IAM Access Advisor' lets us view the permissions who are unused by users.

The shared responsibility model of AWS states that amazon is responsible for the cloud infrastructure but the client is responsible for how its being used and thus for the creation of users, groups, password policies, MFA as found in the IAM service.

### Elastic Compute Cloud (EC2)
To avoid spending excessive money you can indicate a budget limit on the AWS platform to notify you when it gets exceeded.

EC2 is one of the most popular services. It is the IaaS offering of AWS.<br>
Multiple possibilities exist with it, you can rent virtual machines (EC2), store data on virtual drives (EBS), distribute load across machines (ELB), scale the services using an auto-scaling group (ASG).<br>
On our EC2 we can use as operating systems, Linux, Windows or Mac OS. We can indicate how much CPU, RAM and storage space we want. Also network card and firewall rules.<br>
The 'EC2 User data' script allows us to bootstrap our instances. Bootstrapping means launching commands when a machine starts.

Different types of EC2 instances exist.<br>
![Screen Shot 2024-05-14 at 16 34 57](https://github.com/artainmo/DevOps/assets/53705599/f51660a3-e359-4c30-b80f-2bce42a067d9)<br>
When for example taking the name 'm5.2xlarge'. 'm' stands for the instance class, '5' for hardware generation and '2' for instance size.<br>
EC2 instance types include 'general purpose', 'compute optimized', 'memory optimized' for processing large datasets in memory, 'storage optimized' for high read and write access to large datasets on local storage.

Security groups control how traffic is allowed in and out of our EC2 instances. They are defined by 'allow' rules and act like a firewall on EC2 instances.

SSH allows the control of a remote machine using the command line. SSH is used to connect inside our EC2 instance safely.<br>
An easier alternative is to use via AWS platform the EC2 instance connect.

Usually on-demand instances are used, however, other purchasing options exist. Reserved instance is useful for long workloads of 1-3 years. Savings plan instance is for long workloads too but also comes with a commitment to a certain amount of usage. Spot instance is for short workloads, it is cheaper but less reliable. Dedicated hosts allow to book an entire physical server. Capacity reservations reserve capacity in a specific AZ for any duration.<br>
Here is the price comparison.<br>
![Screen Shot 2024-05-14 at 18 38 32](https://github.com/artainmo/DevOps/assets/53705599/6f83530b-dd86-4cfe-a90c-40c0af58d748)

The shared responsibility model of AWS states that amazon is responsible for the infrastructure while the client is responsible for the security group rules, operating-system updates and in general all the utilities installed on the EC2 instance.

### EC2 instance storage
Elastic Block Store (EBS) volume is the most important storage option in EC2. It allows to persist data even after termination of the instance. It can quickly be detached from one EC2 instance and attached to another one within the same AZ.<br>
When creating an EBS we have the 'Delete on Termination' option that is activated by default for the root volume but not other volumes. Thus if you want to preserve the root volume after instance termination you need to deactivate this option.

## Resources
[Udemy course - AWS certified cloud practitioner](https://campus19.udemy.com/course/aws-certified-cloud-practitioner-new)<br>
