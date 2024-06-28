# Cloud

## Table of contents
- [Udemy course - AWS certified cloud practitioner](#Udemy-course---AWS-certified-cloud-practitioner)
  - [What is cloud computing?](#what-is-cloud-computing)
  - [AWS cloud overview](#AWS-cloud-overview)
  - [Identity and Access Management (IAM)](#identity-and-access-management-iam)
  - [Elastic Compute Cloud (EC2)](#elastic-compute-cloud-ec2)
  - [EC2 instance storage](#EC2-instance-storage)
  - [Elastic Load Balancing (ELB) & Auto Scaling Groups (ASG)](#elastic-load-balancing-elb--auto-scaling-groups-asg)
  - [Amazon S3](#Amazon-S3)
  - [Databases & Analytics](#databases--analytics)
  - [Other Compute Services: ECS, Lambda, Batch, Lightsail](#other-compute-services-ecs-lambda-batch-lightsail)
  - [Deployments & Managing Infrastructure at Scale](#deployments--managing-infrastructure-at-scale)
  - [Leveraging the AWS Global Infrastructure](#Leveraging-the-AWS-Global-Infrastructure)
  - [Cloud Integration](#Cloud-Integration)
  - [Cloud Monitoring](#Cloud-Monitoring)
  - [Virtual Private Cloud (VPC) & Networking](#virtual-private-cloud-vpc--networking)
  - [Security and Compliance](#Security-and-Compliance)
  - [Machine Learning](#Machine-Learning)
  - [Account Management, Billing and Support](#account-management-billing-and-support)
  - [Advanced Identity](#Advanced-Identity)
  - [Other Services](#Other-Services)
  - [AWS Architecting and Ecosystem](#AWS-Architecting-and-Ecosystem)
- [Udemy course - AWS certified machine learning specialty](#Udemy-course---AWS-certified-machine-learning-specialty)
  - [Data Engineering](Data-Engineering)
- [Resources](#Resources)  

## Udemy course - AWS certified cloud practitioner
Other cloud providers than amazon exist. Here, we will specifically learn how to use AWS. However, this knowledge can also be applied to other cloud platforms.

In this course 40 amazon web services (AWS) out of 200+ will be covered. The 'cloud practitioner' certificate is foundational. It can be followed by other certificates, usually the 'solutions architect' which contains more practice, and lastly a specialty certificate such as the 'machine learning' or 'security' AWS certificate.

To use amazon's cloud products we first need to create an AWS account to then access the AWS platform.

### What is cloud computing?
A server is necessary to host a website, contains central processing units (CPU) to compute and random-access memory (RAM) for memory that can be stored and retrieved quickly. A server can also have a database for long-term data storage and routers, switch, DNS server for networking.

In the past own website would run on own server(s). This comes with downsides such as costs related to buying servers, space, power supply, maintenance, infrastructure monitoring, scaling or replacing hardware takes more time and is more complicated.<br>
The cloud resolves those problems by allowing rental of external servers and thus delegation of associated tasks.

![Screen Shot 2024-05-22 at 12 56 22](https://github.com/artainmo/DevOps/assets/53705599/6cb8db76-1f74-4ace-8f3d-e20efab8115e)

Cloud computing is the on-demand delivery of computing power, database storage, applications, and other IT resources.<br>
Via a web-application you can indicate how much cloud computing resources you need. Usually with cloud platforms you only pay for what you use which we call pay-as-you-go pricing. 

Netflix and dropbox are examples of services who are built on AWS.

Private cloud are cloud services used by a single organization. While public cloud is delivered to the public via internet. AWS, Microsoft Azure and Google cloud are public clouds. Hybrid clouds have some own servers to store sensitive assets while it also uses a public cloud.

Different types of cloud computing exist. Infrastructure as a service (IaaS) provides the hardware only, thus you can install your own OS and other programs on it. Platform as a service (PaaS) also provides the DevOps so the client is only responsible for the data and applications/code. Lastly, software as a service (SaaS) is a complete product that is run and managed by the service provider.<br>
![Screen Shot 2024-05-14 at 11 29 32](https://github.com/artainmo/DevOps/assets/53705599/73284c98-a2b2-4fd0-a10f-4f67f48d50b9)<br>
'Amazon EC2' is an AWS service example of IaaS. 'Elastic Beanstalk' is an AWS service example of PaaS. Heroku is another service that provides PaaS. Many AWS services are SaaS, for example Rekognition for machine-learning (ML) provides a pre-trained model.

### AWS cloud overview
In 2002 the cloud at amazon was internally launched. In 2003 they had the idea of sharing with others and in 2004 they launched their cloud publicly.<br>
In 2019 AWS accounted for 47% of the market with microsoft being second at 22%.

AWS enables users to build scalable applications in a diverse set of industries. Its use cases include hosting of websites or mobile apps, gaming, enterprise IT, big data analytics.

At AWS we pay for compute time and amount of stored data.

AWS is global.<br>
It has regions all over the world with regions referring to clusters of data centers. Due to legal reasons when launching a new application you may need to choose a local region. Else it is best to choose a region close to customers to reduce latency. Available services and pricing can also be variable across regions.<br>
Each region has a minimum of three availability zones (AZ). Each AZ consists of one or more separate data centers so that if one fails another AZ can be used instead.<br>
AWS has more than 400+ points of presence in 90+ cities across 40+ countries which allows content delivery to end users with lowest latency possible.

The shared responsibility model defines the distribution of responsibilities for security in the AWS cloud. The client is responsible for data and AWS for cloud.

The Acceptable Use Policy describes prohibited uses of the web services offered by Amazon Web Services.

### Identity and Access Management (IAM)
IAM is a global service, meaning it is available in all regions. Other global services are CloudFront, Route 53, and WAF.

When you create an AWS account you are the root user. However, it is best practice to work via admin users who don't have all permissions.
IAM service allows the creation of users and groups in our AWS account for them to have certain permissions or not on our AWS account. Those permissions can be defined in a JSON document we call a 'policy'. The 'least privilege' principle should be used, it means a user should not receive more permissions than necessary.

![Screen Shot 2024-05-14 at 14 27 17](https://github.com/artainmo/DevOps/assets/53705599/4b425dce-83ae-4c9d-abea-389fb6fdcd61)

To protect your users you can also create password policies which define how strong the users' passwords must be, if users can/must change their password and so on.<br>
For ideal security you can use multi-factor authentication (MFA) which consists of a regular password next to a security device you own. In AWS, MFA devices can be virtual such as Google Authenticator or Authy which we call virtual MFA devices, else they can be physical such as Hardware MFA device or UTF security key. Hardware MFA device is a hardware device unique to its user that generates a six-digit numeric code. UTF security key is a device that you plug into a USB port on your computer.

In the AWS platform you can create policies and associate them with specific users or groups. Users can be associated with groups and thus policies associated with a group would apply to all the users within that group.

AWS can be accessed via the management console, thus the online platform protected by password and MFA. But also via a command line interface (CLI) which is protected by access keys. Lastly, the software developer kit (SDK) which is used when calling AWS APIs from your application code and is also protected by access keys.<br>
Access keys are long-term credentials for an IAM user or the AWS account root user.<br>
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
When creating an EBS we have the 'Delete on Termination' option that is activated by default for the root volume but not other volumes. Thus if you want to preserve the root volume after instance termination you need to deactivate this option.<br>
It is possible to make EBS backups, also called snapshots. Those snapshots can also be copied to other AZs or regions to leverage the global infrastructure.<br>
EBS volumes cannot be accessed simultaneously by multiple EC2 instances.

Amazon machine image (AMI) represents a customization of an EC2 instance. Thus it contains pre-packaged customized software to boot the EC2 instance faster.<br>
The AMI must be in the same region as that of the EC2 instance to be launched. If the AMI exists in a different region, it can be copied to the region of the EC2 instance. The region of AMI has no bearing on the performance of the EC2 instance.<br>
Some AMIs are public and provided by AWS, but you can also create your own AMIs. You can also sell your AMIs on an AWS Marketplace AMI.

EC2 Image Builder is a new service that can automate the creation of virtual machines or container images. It can automate the creation, maintenance and testing of EC2 AMIs.

EBS volumes are network drives with good but limited performance. EC2 Instance Store can be used instead when needing a high-performance hardware disk with better I/O performance. Its storage is lost if it is stopped, thus EBS is better for long-term storage.

Elastic File System (EFS) is a third storage type for EC2. It is a shared network file system (NFS) that you can mount to 100s of EC2. It only works with Linux EC2 instances and it works across multiple AZs.<br>
EFS Infrequent Access (EFS-IA) is a storage class who is cost optimized for files you don't access daily. It is less expensive than EFS Standard. By enabling it, EFS will move infrequently accessed files to EFS-IA. A Lifestyle Policy can be enabled, indicating when to move unaccessed files to EFS-IA.

Amazon FSx is a service to get third-party high-performance file systems on AWS. 'FSx for Windows File Server' is meant for Windows instances. 'FSx for Lustre' is used on Linux for high-performance computing such as machine-learning, analytics, video processing.

The shared responsibility model of AWS states that amazon is responsible for the infrastructure, data replication and privacy while the client is responsible for creating backups/snapshots and encrypting data.

### Elastic Load Balancing (ELB) & Auto Scaling Groups (ASG)
In AWS, vertical scalability means increasing the size of the instance. By for example going from using t2.micro to using t2.large.<br>
Horizontal scalability consists of increasing the number of instances in AWS. It implies the use of distributed systems. Horizontal scalability enables high availability which should consist of running an application in at least 2 AZs. Because if one AZ is down the other is still running.

Scalability is the ability to accomodate a larger load by making the hardware stronger (scale up) or by adding nodes (scale out). Once a system is scalable, elasticity means that there will be some 'auto-scaling' so that the system can scale based on the load to match the demand and optimize costs.

Load balancing allows elasticity by being a server that forwards internet traffic equally to multiple servers (EC2 instances) downstream. Thus it balances the traffic/load across multiple running instances of an application. It does health-checks and if one instance fails it can forward to other instances in other AZs making the application highly-available.<br>
AWS provides as service the elastic load balancer (ELB), being a managed load balancer. Multiple types exist.<br>
![Screen Shot 2024-05-15 at 13 29 04](https://github.com/artainmo/DevOps/assets/53705599/b7b86737-71cf-4973-b167-1a2a4d20c439)

Website load can change over time. The goal of an ASG is to scale out (add EC2 instances) or scale in (remove EC2 instances) to match an increased or decreased load respectively. This comes with cost savings and can automatically replace unhealthy instances and connect new instances to the ELB. You can define a minimum and maximum number of running EC2 instances.<br>
Different scaling strategies exist, such as manual scaling or dynamic scaling. Dynamic scaling can be further divided into Step scaling whereby rules can be created about adding/removing units relative to used CPU, Target Tracking scaling where an average CPU usage should be maintained over time, Scheduled scaling which anticipates scaling needs based on usage patterns, and Predictive scaling that uses machine learning to predict future traffic and thus scaling needs.

### Amazon S3
Amazon S3 is at its core an infinite storage. It is used for storage and backup. You can also store and host static websites on it.<br>
Amazon S3 stores files/objects into directories/buckets. Buckets must have a globally unique name and is defined at the region level.<br>
What we call objects are files who have a key. This key is the path of the file. The object value is the content of file body which can be everything you want but has a size limit of 5TB, if larger than that you must use 'multi-part upload'.

S3 bucket policies are used for S3 security. They are JSON based and can be used to grant public access to the bucket, force object encryption, or to grant access to another account (Cross Account).

Versioning files in S3 enables for example updating of static websites. It protects against unintended deletes or faulty additions by being able to restore previous versions.

Cross-region replication (CRR) and same-region replication (SRR), as the name implies is related to S3 replication through a different or the same region. S3 replication synchronizes buckets. Thus it duplicates a bucket and then updates it if new version of initial bucket is created.

S3 has different storage classes. What differentiates them is that the more expensive ones return your stored data faster and/or more often.<br>
It is possible to move between them manually or using S3 Lifecycle configurations.<br>
Durability indicates how often data is lost and is similar between storage classes. Availability indicates how readily available a service is which in AWS usually is 99.99%.<br>
The Standard storage class is general purpose.<br>
The Infrequent Access storage class is for data that is less frequently accessed but when needed requires rapid access. It is cheaper than Standard storage class. One-Zone Infrequent Access is cheaper than Standard Infrequent Access.<br>
The Glacier storage class is low cost and meant for archiving/backup. You pay for storage and object retrieval. It has the 'Instant Retrieval' option and 'Flexible Retrieval' option with different retrieval time options of 5min to 12hours.<br>
S3 Glacier Deep Archive is Amazon S3’s lowest-cost storage class and supports long-term storage for data that may be accessed once or twice in a year. It is designed for customers in highly-regulated industries, such as the Financial Services, Healthcare, and Public Sectors, that retain data sets for 7-10 years or longer to meet regulatory compliance requirements. S3 Glacier Deep Archive can also be used for backup and disaster recovery use cases. It has a retrieval time of 12 to 48 hours.<br>
The last storage class is Intelligent-Tiering which allows you to automatically move between storage classes based on usage.

Server-side encryption means that the uploaded file/object on S3 will get encrypted automatically by the server. Client-side encryption is when the user encrypts the file/object before uploading it. Both exist on AWS but by default server-side encryption is always on for S3.<br>
If needing encryption before it is sent to S3, server-side encryption is not sufficient, then we need client-side encryption. For this we can use AWS encryption SDK.<br>
All S3 storage classes, such as Glacier, have by default server-side encryption, CloudTrails and AWS Storage Gateway too because they use S3 for storage.

IAM Access Analyzer is a monitoring feature to ensure that only intended people have access to S3 buckets. It works by analyzing the various related policies. It will indicate what buckets are publicly available or shared with whom.

The shared responsibility model of AWS states that amazon is responsible for the infrastructure while the client is responsible for S3 versioning, bucket policies, replication setup and data encryption.

AWS Snow Family represents a highly-secure, portable/offline device to collect and process data at the edge, and migrate data into and out of AWS.<br>
The edge refers to a location where internet is limited to non-existent, this makes online data uploads and processing too slow to impossible. Examples are a truck on the road, ship on the sea, an underground mining station. This is why Snow Family devices are used to process data, and store data to upload in the actual S3 cloud later by shipping the device to it.<br>
Edge computing is processing data while it is being created in an edge location.
For data migration we have the following devices in ascending order of storage capacity, the Snowcone (8TB storage), Snowcone SSD (14TB), Snowball Edge (petabytes of storage) and Snowmobile (exabytes of storage). While for edge computing, only the Snowcone and Snowball Edge can be used.<br>
AWS OpsHub is a software with a UI to use your AWS Snow Family device.<br>
For Snowball Edge you pay for device usage and data transfer out of AWS.

AWS Storage Gateway is used to bridge on-premise data and cloud data in S3 when using a Hybrid Cloud. It allows on-premise to seamlessly use the AWS Cloud. It can be used for creating and restoring backups.<br>
It supports the Tape, File and Volume Gateways.

### Databases & Analytics
Storing data on disk as with EFS, EBS, EC2, Instance Store and S3 can have its limits. This is why you sometimes want to store data on a database where you can structure the data, build indexes for efficient database searches, and define relationships between datasets.<br>
Relational databases enable linking datasets and the use of SQL queries.<br>
NoSQL/shemaless databases are non-relational and don't use SQL. They are flexible and scalable. Different types exist for optimization of specific data models.

Amazon Relational Database Service (RDS) is a managed service for the use of a SQL database in the cloud. We can also deploy own databases on EC2. But the advantage of RDS is that it is managed by Amazon which leads to improved performance compared to a customer-managed database instance.<br>
Amazon Aurora is a database technology who supports PostgreSQL and MySQL, because it is cloud optimized, performances on PostgreSQL and MySQL is more efficient. It is more expensive than RDS but more efficient. Aurora is serverless and managed by RDS. The AWS Product team is responsible for applying patches to the underlying OS for AWS Aurora.

RDS Read Replicas can scale the read workload of your database thus they improve database scalability.<br>
Multi-AZ gives high availability by providing a replication of the database into another AZ.<br>
Multi-Region creates Read Replicas across regions which is useful for disaster recovery and local performance for global reads.

Amazon ElastiCache is used for managed Redis or Memcached databases. Those databases are cache-based which we call in-memory database. Caches have low latency but smaller storage capacity. Thus ElastiCache is fast but of smaller capacity like a RAM in a computer.

DynamoDB is a managed, NoSQL, highly-available, serverless database with replication across 3 AZs. It can scale automatically and has low retrieval latency. It is a key-value and document database with a flexible shema. DynamoDB provides the least amount of operational overhead compared to other databases.<br>
DynamoDB Accelerator (DAX) is a managed cache for DynamoDB. Thus as it uses cache it is 10X faster.<br>
DynamoDB Global Tables make a DynamoDB table accessible with low latency in multiple regions.

Redshift is a database type based on PostgreSQL designed for large scale data set storage and analysis. It acts as a data warehouse which is a central repository containing data from one or more disparate sources. It is not used for online transaction processing (OLTP), which is what RDS is good for. Instead Redshift is used for online analytical processing (OLAP).

Elastic MapReduce (EMR) helps create Hadoop clusters to analyze and process vast amounts of data. Those clusters can be made of 100s of EC2 instances. It is used for machine learning, web indexing, big data.

Amazon Athena is a serverless query service to perform analytics against S3 objects. It uses standard SQL language. It is used for reporting and querying ELB Logs.

Amazon QuickSight is a serverless machine-learning-powered business intelligence service to create interactive dashboards of a database to visually represent the data.

DocumentDB is a database technology who supports the NoSQL database MongoDB. MongoDB uses data in JSON format. It is managed and replicated across 3 AZs.

Amazon Neptune is a managed graph database. A social network is an example of a graph dataset. It is available across 3 AZs with up to 15 read replicas.

Amazon Timestream is a managed, fast, scalable and serverless time series database. Time series data is data who is evolving over time. It is 1000s times faster and 1/10<sup>th</sup> the cost of relational databases. It also has built-in time series analytics functions.

Amazon Quantum Ledger Database (QLDB) holds a ledger which is a book recording financial transactions. It is managed, serverless, and has replications across 3 AZ. Entries are immutable as they cannot be removed or modified as do financial transactions. Data can be manipulated using SQL and performance is 2-3X better than common ledger blockchain frameworks. Contrary to Amazon Managed Blockchain there is no decentralization with QLDB.

The blockchain makes it possible to build applications where multiple parties can execute transactions without the need for a trusted, central authority. The blockchain is decentralized.<br>
Amazon Managed Blockchain is a managed service to join public blockchain networks or create your own private network. It is compatible with two blockchain frameworks, Hyperledger fabric and Ethereum.

AWS Glue is a extract, transform and load (ETL) service. ETL is used to prepare and transform datasets. It is managed and serverless.<br>
It is able to extract data from S3 buckets or databases to transform them and load them in another database to perform analytics.<br>
AWS Glue Data Catalog is a central repository to store structural and operational metadata for all your data assets.

Database migration service (DMS) is a service that migrates data from one database (DB) to another. DMS runs in an EC2 instance, extracts datas from the source DB and inserts it in the target database.

### Other Compute Services: ECS, Lambda, Batch, Lightsail
Docker is a software development platform to deploy apps in containers. With containers being virtual environments that run on an OS thus that do not manage own OS. By not managing own OS they are lightweight. Their utility lies in automating the creation of a particular environment which is defined in an image.<br>
Elastic container service (ECS) launches docker containers in AWS EC2 instances. It integrates with the Application Load Balancer.<br>
Fargate is also used to launch Docker containers on AWS but you don't need to provision the infrastructure (EC2 instances).<br>
Elastic Container Registry (ECR) is used to store docker images so that they can be run by ECS or Fargate.

When using the word 'serverless' it means the developers don't need to manage the servers anymore, instead they can just deploy code. It does not mean there are no servers, instead it means the client does not need to manage them.

AWS Lambda is serverless and executes virtual functions to perform a task.<br>
A common example is to use lambda for a serverless thumbnail creation service, where uploading an image into an S3 bucket will trigger a Lambda function that transforms the image into a thumbnail who is then pushed back into the S3 bucket.<br>
It integrates with all other AWS services and scales automatically. You pay per lambda call and compute time duration.

To build a serverless API with Lambda we need to expose the Lambda service as an API. This is why we need to expose it via an Amazon API Gateway. The client will then be able to communicate using the API to the API gateway which will proxy requests to the Lambda service.<br>
This API Gateway is serverless and scalable. It supports RESTful and WebSocket APIs.

AWS Batch is a scalable and managed batch processing service. It can run 100,000s of computing batch jobs on AWS. A batch job is a job with a start and end, thus it is not continuous. Batch jobs are defined as Docker images and run on ECS.<br>
Lambda and Batch both execute functions/jobs. They differ in that Lambda has a time and disk space limit while batch has no such limits. However, Lambda is serverless while Batch relies on EC2.

Amazon Lightsail gives access to virtual servers, storage, databases and networking in one place. The pricing is low and predictable. It is used because it is simpler than setting up separate services such as EC2, RDS, ELB and so on. Thus it is good for people with little cloud experience. It has high availability but no auto-scaling. It is good for simple applications, websites or dev/test environments.

### Deployments & Managing Infrastructure at Scale
CloudFormation is a declarative way of outlining your AWS infrastructure as code and build it. Declarations of the AWS resources are made in JSON or YAML and are called CloudFormation Templates.<br>
A CloudFormation Template can be visualized using the Application Composer service.

AWS Cloud Development Kit (CDK) is a way of defining your cloud infrastructure via a familiar programming language such as javascript, python, Java. This code will then be compiled into a CloudFormation template. 

When deploying an application on AWS we usually follow a 3-tier architecture. The user connects to a load balancer that can be in multiple availability zones. This load balancer will forward traffic to multiple EC2 instances who are managed by an ASG. Those EC2 instances are usually connected to a regular database like RDS and eventually also to a fast database like ElastiCache. Usually when searching data, first it will be searched in the fast chached database and afterwards in the regular database.<br>
This architecture can be reproduced automatically using AWS Elastic Beanstalk. Which is a developer centric view of deploying and scaling an application/service on AWS. It is a PaaS because the client only needs to manage the applications and the data. It is limited to certain programming languages or Docker. Elastic Beanstalk automatically handles the deployment details of capacity provisioning, load balancing, auto-scaling, and application health monitoring.<br>
CloudFormation and Elastic Beanstalk are free of use, but you do pay for the resources created.

AWS CodeDeploy automatically deploys or upgrades applications. It works both for EC2 instances and on-premises servers, thus it is a hybrid service.

Before pushing application code to servers you need to store it somewhere. Usually in a git repository like Github. AWS has a competing product called CodeCommit.

AWS CodeBuild allows to build code in the cloud. It compiles source code, run tests, and produce packages who are ready for deployment. In practice, CodeBuild will retrieve the code from CodeCommit, run defined scripts, build the code, to produce a ready to deploy artifact.<br>
CodeBuild is managed, serverless, scalable and secure. You pay as you go.

CodePipeline can be used to connect CodeCommit, CodeBuild and CodeDeploy. CodePipeline automates the steps necessary to push code to production. Those steps are to get the code, build it, test it, provision servers for it and deploy on those servers. It is basically used for CI/CD.

Software packages have dependencies, meaning they depend on each other to be build. Artifact management refers to storing and retrieving those dependencies. AWS CodeArtifact is an artifact manager for software development. Developers and CodeBuild can then retrieve dependencies straight from CodeArtifact.

AWS CodeStar is a unified UI to easily manage software development activities in one place. This is useful when needing to work with the different services used for CI/CD such as CodeCommit, CodeBuild, CodeDeploy, CodePipeline.<br>
It can also be used to edit the code directly in the cloud using AWS Cloud9. AWS Cloud9 is a cloud integrated development environment (IDE), for writing, running and debugging code.

AWS Systems Manager (SSM) allows centralization of operational data from multiple AWS services and automate tasks across AWS resources. It manages both EC2 and on-premise systems at scale, thus it is a Hybrid service. It gives operational insight about the state of the infrastructure, it automates patches, it runs commands across all servers and stores parameter configuration with the SSM Parameter Store.<br>
To use SSM we need to install the SSM agent onto our EC2 instances or on-premise system.<br>
SSM has a feature we call SSM Session Manager. It starts a secure shell on EC2 or on-premise servers without the need for SSH.<br>
SSM Parameter Store allows secure storage of configurations and secrets on AWS such as API keys, passwords.

### Leveraging the AWS Global Infrastructure
A global application is an application deployed onto multiple AWS regions or edge locations. The advantage is decreased latency via local deployments being present. Another advantage is Disaster Recovery because if one region goes down, others are still available, this increases the availability of the application. A distributed global infrastructure is also harder to attack.<br>

Route 53 is an AWS service that routes users to the closest deployment with least latency. It is a managed Domain Name System (DNS). DNS associates servers' IPs and URLs.<br>
A web browser first makes a DNS request with an URL to Route 53. Route 53 will return the associated IP address. The web browser will then make its request to the IP address which will return an HTTP response.<br>
Route 53 has different routing policies. The 'Simple Routing Policy' has no health checks and simply returns an IP when a URL gets sent to it. The 'Weighted Routing Policy' distributes traffic across multiple EC2 instances which is similar to load balancing and thus health checks are used. The 'Latency Routing Policy' makes users connect to the closest servers to minimize latency. The 'Failover Routing Policy' performs health checks on primary server and redirects traffic to the failover server if the primary server failed its health checks with the goal of handling disaster recovery.<br>
Route 53 has the following features, Domain Registration, DNS, Health Checks, Routing Policy.

CloudFront is a Content Delivery Network (CDN). It replicates part of applications to edge locations to decrease latency. It will also cache common requests to decrease latency further. It has 216 points of presence representing edge locations globally.<br>
If a client makes a request to a CloudFront edge location, it will first search if it has the response in the cache, if not it will retrieve the response in the origin instance and cache it locally for future similar requests.<br>
CloudFront protects against web attacks by using AWS WAF and AWS Shield.

S3 buckets are only linked to one region. Thus transferring data to it can be slow from certain locations. S3 Transfer Acceleration is used to accelerate global uploads and downloads into S3. This is done by uploading to a local edge location and subsequently let the edge location transfer the file via internal network to the S3 bucket.

AWS Global Accelerator improves global application availability and performance via the AWS global network. It leverages the AWS internal network to optimize by 60% the route to your application. The application gets accessed through two static IPs we call Anycast IPs which redirect automatically to the correct edge location which will finally send the traffic to the application.

Hybrid clouds have differing ways of dealing with the cloud infrastructure and on-premise infrastructure. AWS Outposts consists of 'server racks' that offer the same AWS infrastructure, services, APIs and tools to build your own applications on-premise just as in the cloud. This makes dealing with the cloud or on-premise infrastructures homogeneous and also facilitates migration of on-premise to cloud.

WaveLength Zones are infrastructure deployments embedded within the telecommunications providers' datacenters at the edge of 5G networks. It brings AWS services to the edge of the 5G networks. As a result those services will have ultra-low latency when accessed via the associated 5G network. Amazon Wavelength thus provides low latency to applications via 5G networks.

AWS Local Zones allow you to place compute, storage, database, and other AWS services closer to end users to run latency-sensitive applications. It extends regions and AZs.

An application deployed in a single region and single AZ is easy to setup but does not have high availability and neither low global latency. When in a single region but multiple AZs the availability is high but global latency still isn't low.<br>
Next we have a multi-region architecture called Active-Passive which means we have two regions with each having one or multiple AZ. In one region our EC2 instance will be active which means users can both read and write to that instance. The EC2 instance in the other region is passive which means it has been replicated from the active region, can be read by users but writing to the instance is not possible. Active-Passive comes with improved global read latency but not global write latency.<br>
Another multi-region architecture is called Active-Active. Where each EC2 instance can take both writes and reads while replication is still present. This improves read and write latency but is more difficult to setup.

### Cloud Integration
When we start deploying multiple applications, they will inevitable need to communicate with one another.<br>
A synchronous communication consists of having one application communicate with another application in a direct way.<br>
Asynchronous or event-based communication consists of an application not being in direct contact with another application, as a queue where the request of first application lies bridges the connection with other application that can read from that queue.<br>
Synchronous communication can be problematic during sudden traffic spikes. In such a case it is better to decouple the application using a queue model like SQS or a pub/sub model like SNS or a data-streaming model like Amazon Kinesis. Those services can scale independently from our application.

Amazon Simple Queue Service (SQS) allows application decoupling. It does this by using a queue that lies between first and second application. The first application will send data into the queue while the second application will extract those datas from the queue. Multiple applications can send into the queue and multiple applications can extract from the queue which allows for scaling.<br>
First in first out (FIFO) is a way of ordering messages in the queue. With Amazon SQS FIFO Queues the messages will be in order.

Amazon Simple Notification Service (SNS) is the second way to decouple our applications. It uses a pub/sub model.<br>
![Screen Shot 2024-05-17 at 18 35 43](https://github.com/artainmo/DevOps/assets/53705599/1fc921d2-ccaa-469e-a1b3-6e50743d16a0)<br>
The 'event publishers' only send messages to one SNS topic. While as many 'event subscribers' as we want can listen to the SNS topic notifications. Each subscriber to the topic will get all the messages.

Amazon Kinesis is a managed service to collect, process and analyze real-time streaming data at any scale.

On-promise architectures don't use AWS services for application decoupling. They use open protocols like MQTT and others. When migrating to the cloud, instead of modifying the application for handling SQS or SNS, we can use Amazon MQ. It is only used by migrating companies that need to keep using open protocols as Amazon MQ has the downside of not being able to scale as much as SQS or SNS.

### Cloud Monitoring
Cloud monitoring consists of overviewing our cloud performance.

Amazon CloudWatch Metric provides metrics for every service in AWS. You can create own CloudWatch dashboard of metrics.<br>
The Billing Metric is popular and reflects how much you have spent on AWS each month. Other important metrics are for our EC2 instances for examle, CPU utilization, status checks (verifies instance functions properly), network (to see how much network goes in and out of our instance). For our EBS volumes we can look at disk read/writes. For S3 buckets we can look at bucket size in bytes, number of objects and requests.<br>
CloudWatch Alarms can be used to trigger notifications for any metric after it surpasses a certain treshold.

When an application runs, it logs in a file what it is doing. Those log files can be collected and used when wanting to troubleshoot an application.<br>
Amazon CloudWatch Logs collects those log files from various AWS services/applications but also on-premise servers. CloudWatch log agents can be used on EC2 instances or on-premise servers for them to create collectable log files. It centralizes the logs from all of your systems.

Amazon EventBridge (formerly known as CloudWatch Events) allows reactions to events happening in AWS account. Using Cron Jobs you can react to events every x amount of time. Else we can create rules to react to a service doing something. A reaction can be calling a lambda function for example or send a notification using SNS.<br>
Events happening from within AWS services are called 'Default Event Bus'. It is also possible to get events from AWS partners which we call 'Partner Event Bus'. Lastly, own custom applications can also send events which we call 'Custom Event Bus'.

AWS CloudTrail is a service enabled by default that provides governance, compliance and audit for own AWS account. It gets the history of events/API-calls made within AWS account by the console, SDK, CLI, AWS services. Those logs can be sent to CloudWatch Logs or S3.<br>
CloudTrail Insights provides automated analysis of CloudTrail Events.<br>
If a resource gets deleted in AWS, CloudTrail should be consulted first as it records the history of events/API-calls made which will help determine who or what deleted the resource.<br>
CloudWatch, CloudTrail and Config can be differentiated as follows. CloudWatch is for resource performance monitoring, events, and alerts. CloudTrail is for account-specific activity and audit. Config is for resource-specific change history, audit, and compliance.

Debugging on distributed systems is hard because log formats differ across applications and log analysis is hard. AWS X-Ray resolves this problem by providing a visual analysis of own applications after tracing requests made through the distributed applications.

Amazon CodeGuru is a machine-learning-powered service for automated code reviews (CodeGuru Reviewer) and application performance recommendations (CodeGuru Profiler).

AWS Health Dashboard consists of two parts, a Service History and your Account.<br>
The Service History, AWS Service Health Dashboard, shows all regions' and services' health information up-to-the-minute.<br>
Your Account, AWS Personal Health Dashboard, provides alerts and remediation guidance when AWS is experiencing events that may impact own infrastructure. It provides a personalized view of the performance and availability of the AWS services personally used.

### Virtual Private Cloud (VPC) & Networking 
EC2 instances get a new public IP address every time you stop and restart them. However, private IP addresses are fixed for EC2 instances even if you start/stop them. AWS also has an Elastic IP which can attach a fixed public IPv4 to an EC2 instance.<br>
For public IPs both IPv4 and IPv6 can be used. While IPv4 only allows for private IPs. However, IPv4 costs $0.005 per hour while IPv6 is free.

A VPC is a private network to deploy own resources, for example EC2 instances. One VPC is linked to one region, thus when using multiple regions you will also need multiple VPCs.<br>
Within a VPC we can find Subnets which partitions own network inside own VPC. One Subnet is associated with one AZ and can launch EC2 instances. A public Subnet is accessible from the internet while a private Subnet is not. Route Tables are used to define access to the internet and between Subnets.<br>
A VPC contains a CIDR Range which indicates the range of allowed IP addresses within the VPC.<br>
Internet Gateways help our VPC instances connect with the internet. Public Subnets have a route to the internet gateway. NAT Gateways allow instances in Private Subnets to access the internet while remaining private.

Network ACL (NACL) is a stateless firewall which controls traffic from and to the Subnet. It can have 'allow' and 'deny' rules that include IP addresses.<br>
Security Groups is a stateful firewall that controls traffic to and from an EC2 instance or ENI. It can have 'allow' rules that include IP addresses and other security groups.

Flow Logs capture information about IP traffic going into your interfaces. It helps monitor and troubleshoot connectivity issues.<br>
We can have VPC Flow Logs, Subnet Flow Logs and Elastic Network Interface Flow Logs with the last one being related to EC2 instances. But we can also get network information from ELB, ElastiCache, RDS, Aurora...<br>
Log data can go to S3, CloudWatch Logs, and Kinesis Data Firehose.

VPC Peering connects two VPCs privately using AWS' network to make them behave as if they are in the same network. For this to work the CIDR Range must not overlap.

VPC Endpoints enable connection to AWS services privately. By using a private network, security is enhanced and latency lowered.<br>
There are two types of VPC endpoints: interface endpoints and gateway endpoints.<br>
Only Amazon S3 and Amazon DynamoDB support VPC gateway endpoint. All other services that support VPC Endpoints use a VPC interface endpoint (note that Amazon S3 supports the VPC interface endpoint as well).


AWS PrivateLink is the most secure and scalable way of exposing a service to 1000s of VPCs. PrivateLink allows you to connect a service running within your VPC to other VPCs directly and privately. With it you can connect to a service in a third party VPC.

A VPN is a connection between on-premise data center and VPC that is encrypted while going over the public internet. Site to Site VPN will connect an on-premise VPN to AWS. A Customer Gateway and Virtual Private Gateway are needed to establish a Site to Site VPN.<br>
Alternatively, Direct Connect establishes a physical connection between on-premise infrastructure and AWS. This connection is private, secure and fast.

AWS Client VPN establishes a connection using OpenVPN from own computer to private network in AWS and on-premises. It allows connection to own EC2 instances over a private IP. The VPN connection is established over the public internet. Thus it provides an OpenVPN connection from own computer to own VPC.

If we have a serious infrastructure on AWS, the network topology can become complicated. Transit Gateway solves this problem by providing peering/connection between thousands of VPC and on-premises using a hub-and-spoke (star) connection.

### Security and Compliance
AWS is responsible for the security of the cloud while customers of the security in the cloud. The client must for example configure the firewall and IAM in the cloud but also encrypt application data.<br>
![Screen Shot 2024-05-18 at 13 20 41](https://github.com/artainmo/DevOps/assets/53705599/124e785e-7b1d-4d03-ac8a-fce1689c7edb)<br>
AWS is responsible for patching and fixing flaws within the infrastructure, but customers are responsible for patching their guest OS and applications. Thus both AWS and the customer are responsible for Patch management. Similarly, configuration management is a shared responsibility. AWS maintains the configuration of its infrastructure devices, but a customer is responsible for configuring their own guest operating systems, databases, and applications.<br>
Customers are responsible for Service and Communications Protection or Zone Security which may require the customers to route or zone data within specific security environments.

A Distributed Denial-of-Service (DDoS) attack on our infrastructure is done by saturating/overwhelming our application server with requests. Those high volume requests occur via bots run on servers.<br>
AWS Shield Standard protects against DDoS attacks, is activated for every AWS customer and is free.<br>
Alternatively, AWS Shield Advanced offers premium DDoS protection is optional and costs $3000/month. With Shield Advanced AWS reimburses costs that incurred during a DDoS attack.<br>
The AWS web application firewall (WAF) can also help protect against common web exploits by filtering HHTP/HTTPS requests based on rules. HTTP/HTTPS requests are part of the Application layer, which is layer 7. WAF can be deployed on Application Load Balancer, API Gateway and CloudFront. It can also be used to block specific geographies.<br>
CloudFront and Route 53 provide availability protection by using the global edge network.<br>
When under attack you must be ready to scale and can use AWS Auto Scaling for that.

AWS Network Firewall provide overall protection of VPCs.

AWS Firewall Manager allows from one place management of all security rules in all accounts of an AWS Organization. It manages VPC Security Groups, WAF rules, AWS Shield Advanced, AWS Network Firewall and others.

Penetration testing consists of attacking own infrastructure to test security. It can be done on AWS. However, certain attacks are prohibited without asking for approval such as DDoS, port flooding, protocol flooding, request flooding, DNS zone walking.

In AWS we can find encryption at rest and encryption in transit.<br>
Data at rest means it is stored on a physical device like a hard drive or S3 bucket. Data in transit means it is moving from one place to another, thus it is being transferred over the network.<br>
Encryption keys are used to encrypt data in both rest and transit states.<br>
AWS Key Management Service (KMS) is a service used to encrypt that manages the encryption keys automatically. Customer managed keys (CMK) are KMS keys in own AWS account that oneself creates, owns, and manages. CloudHSM is another encryption service that differs in that the users need to manage the encryption keys themselves, amazon only provides the dedicated hardware named Hardware Security Module (HSM).

AWS Certificate Manager (ACM) is a service that allows easy provision, management and deployment of SSL/TLS certificates. Those certificates provide in-flight encryption for HTTPS websites.

AWS Secrets Manager is a service that stores secrets. And it can also force the secrets to change every x days.<br>
It can integrate with Amazon RDS so that passwords are created automatically for this database service.<br>
Secrets are encrypted using KMS.

AWS Artifact is a portal that provides customers with on-demand access to AWS compliance documentation (reports) and AWS agreements. These can support internal audits within own company or compliance needs to show company is compliant when using AWS cloud.

Amazon GuardDuty performs intelligent threat discovery to protect an AWS account. It uses ML algorithms and uses as data, CloudTrail Events Logs, DNS Logs, VPC Flow Logs and data from other optional services.<br>
It is great at protecting against cryptocurrency attacks.<br>
EventBridge rules can be setup to create an event in case of findings. This event can trigger a Lamda function or SNS to send notifications.

Amazon Inspector is a service that runs automated security assessments for EC2 instances, container images pushed to ECR, Lambda functions.<br>
Findings can be reported in AWS Security Hub and events of those findings can be created with Amazon Event Bridge.<br>
It evaluates package vulnerabilities for EC2, ECR and Lambda. And network reachability for EC2 only.

AWS Config helps with auditing and recording compliance of your AWS resources. It records configurations and changes over time. This configuration data can be stored in S3 and subsequently analyzed by Athena.<br>
It is a per region service, but you can create multiple Config configurations and then aggregate all the results across regions.

Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect sensitive data in AWS. It can alert users via EventBridge with SNS about sensitive data such as personally identifiable information (PII).

AWS Security Hub is a central security tool to manage security across several AWS accounts and automate security checks. It uses an integrated dashboard to show current security and compliance status.<br>
Services such as Config, GuardDuty, Inspector, Macie, IAM Access Analyzer, AWS Systems Manager, AWS Firewall Manager, AWS Health and AWS Partner Network Solutions, report on one dashboard in AWS Security Hub.<br>
EventBridge can also be used to generate an event on the findings. Amazon Detective can be used to find the source of found issues.

Amazon Detective analyzes, investigates and identifies the root cause of security issues using ML.<br>
It automatically collects and processes events from VPC Flow Logs, CloudTrail, GuardDuty and creates a unified view.

AWS Abuse is used to report AWS resources who are used for abusive or illegal purposes such as spams, port scanning, DDoS attacks, intrusion attemps, hosting illegal content, distribute malware.

The root user is the account owner. It has access to all AWS services and resources. It is not recommended to use the root user. However, certain actions can only be performed by the root user. Such as changing account settings, view certain tax invoices, close the AWS account, restore IAM user permissions, change or cancel AWS Support plan, register as a seller in the Reserved Instance Marketplace, enable MFA on an S3 bucket, edit or delete an S3 bucket policy that includes an invalid VPC ID, sign up for GovCloud.

IAM Access Analyzer is a service that is used to view which resources are shared externally.<br>
You can define a Zone of Trust which refers to all AWS accounts that can be trusted for access. IAM Access Analyzer will report as findings anything outside the Zone of Trust that has access to own AWS services.

### Machine Learning
Amazon Rekognition automates image and video analysis with ML. It can detect and label objects, persons, text and other. It can recognize individuals via facial analysis and search, allowing user verification. It can also capture the path of people in a scene, which we call pathing, and can be useful for sport analysis.

Amazon Transcribe automatically converts speech to text. It uses a deep learning process called automatic speech recognition (ASR). With redaction you can automatically remove PII.

Amazon Polly turns text into speech using deep learning.

Amazon Translate as the name indicates translates languages. It can localize content such as websites or applications and translate text for international users if necessary.

Amazon Lex is the same technology that powers the Alexa device by Amazon. Using ASR it can convert speech to text and using NLP it can understand the text. It can be used to build chat and call center bots. It could also invoke Lambda function as a reaction to what it is being told.<br>
Amazon Connect can be used to build a call center. It is a cloud-based virtual contact center that can receive calls and listen to those calls with Amazon Lex.

Amazon Comprehend is a managed and serverless service used for NLP. It uses ML to find insights and relationships in text.

Amazon SageMaker is a managed service for developers to build own ML models.

Amazon Forecast is a managed service that uses ML to deliver accurate forecasts/predictions. The user only needs to upload his data to S3. Amazon Forecast will then use that data to produce a forecasting model.

Amazon Kendra is a managed document search service powered by ML. It can extract answers from within a document. It can also learn from user feedback to promote preferred results which we call incremental learning.

When buying a product on Amazon, personalized recommendations appear afterwards for the next product you may want to buy. Amazon Personalize is a managed service using ML to produce real-time personalized recommendations.<br>
Personalize can take data from S3 and the Personalize API for real-time data.

Amazon Textract automatically extracts text, handwriting, and data from any scanned document using ML. You can even extract data from forms and tables.

Amazon Bedrock is a service that doesn't need to be known for the exam. It allows building generative AI applications using foundational models like Claude from anthropic, Lama from Meta.<br>
Other ML services exist who are not covered in this course.

### Account Management, Billing and Support
AWS Organizations is a service that allows the management of multiple AWS accounts with the main account being the master account.<br>
One benefit is consolidated billing, meaning across all accounts. Another benefit is discounts from aggregated usage. Reserved instances can be used across all the accounts of the organization. It also contains an API to automate AWS account creation. It also allows restriction of account privileges using Service Control Policies (SCP).<br>
Organizational units (OU) represent a grouping of accounts. They can be nested in each other. The root OU for example contains all accounts and thus nested OUs.<br>
SCP allows whitelisting or blacklisting IAM actions at the account or OU level but the master account it cannot affect. It applies to all Users and Roles of each account. SCP can be used to restrict access to certain services, or enforce PCI compliancy by disabling services.<br>
It is recommended to create accounts per department and to use SCP.<br>
Removing an account from an organization is possible only if the account has the information that is required for it to operate as a standalone account.

Consolidated billing, combines the usage across all AWS accounts in the AWS Organization to share the volume pricing. This combined usage can lead to benefits on discounts. In the end the organization only gets one bill. Reserved instances can be shared across accounts.

AWS Control Tower easily sets up and governs a secure and compliant multi-account AWS environment based on best practices. It automates the set up of AWS Organizations to organize accounts and implement SCPs.

AWS Resource Access Manager (AWS RAM) enables an account to share its resources with another account. Meaning the other account will be able to access and thus modify it.

Users that are new to AWS have too many options and may create stacks that are not in line with the rest of the organization. AWS Service Catalog provides a self-service portal to launch a set of authorized products pre-defined by admins.<br>
Thus the admins must create a collection of products with each product being a CloudFormation template. Afterwards they need to indicate who has access to launch what product. As a user, on Service Catalog, you will see the list of products you are allowed to use.

AWS has 4 different pricing models:<br>
&nbsp;&nbsp;&nbsp;** Pay as you go: Pay for what you use.<br>
&nbsp;&nbsp;&nbsp;** Save when you reserve: Reservations are available for different services such as EC2 Reserved Instances and allow predictable pricing.<br>
&nbsp;&nbsp;&nbsp;** Pay less by using more: Via volume-based discounts.<br>
&nbsp;&nbsp;&nbsp;** Pay less as AWS grows: AWS tends to lower its prices as it grows.<br>
Some services on AWS are free or free up to a certain point. Free services include IAM, VPC, Consolidated Billing, and Elastic Beanstalk.<br>
EC2 on-demand instances are paid per second for Linux/Windows, with minimal use of 60s, or hour for others. If you know you will use EC2 for a long time it is better to use reserved instances for a 1 or 3 year commitment which would be cheaper and comes with no interruptions. EC2, RDS and DynamoDB support reservations to optimize costs. Spot instances are even cheaper (up to 90% discount compared to on-demand) and work by bidding for unused capacity. Dedicated hosts can be reserved as well for 1 or 3 years and are on-demand but are not cost-efficient. They allow use of eligible software licenses. RDS can be used on reserved instances but not on dedicated hosts. Lastly, savings plan is an alternative to save on sustained usage.<br>
Lambda is paid per call and duration.<br>
ECS comes with no cost but runs on EC2 which comes with costs.<br>
With Fargate we need to pay for each container its used CPU and memory as it does not run on EC2.<br>
With S3 you pay for the amount and size of objects and the requests made in and out of S3. You also must pay for data transfer out of S3. But data transfer into S3 is free.<br>
With EBS we have pricing based on the volume type and size. We also pay for backups/snapshots and data transferred out.<br>
For the database service RDS we pay per hour for storage in GB. The price also differs based on the database's characteristics. You can purchase on-demand instances or reserved instances. Backups are free. Input and output requests come with a cost. Again outbound data transfer comes with a cost but inbound or data transfer between other AWS services within the same region are free.<br>
CloudFront's pricing differs across geographic regions. Number of requests are also billed.<br>
Using private IPs instead of public IPs lowers costs and improves network performance. Staying in same AZ lowers costs too.

With Savings Plan, instead of reserving instances you just commit to spending a certain amount of money per hour for the next 1 or 3 years.<br>
With the EC2 savings plan you commit to usage of individual instance families in a region.<br>
With the compute savings plan you don't need to commit to an instance family, region or compute option (EC2, Fargate, Lambda). Thus it is flexible.<br>
The Machine Learning Savings plan is for ML services such as SageMaker.

AWS Compute Optimizer reduces costs and improves performance by recommending optimal AWS resources and resources' configurations for your workloads. It uses ML to analyze resources' configurations and their utilization CloudWatch metrics. It gives recommendations for EBS, Lambda, EC2 and auto-scaling groups.

AWS Pricing Calculator helps estimate costs in the cloud. It is useful both for people who have never used AWS and for those who want to expand their usage.

AWS Billing Dashboard can be used to track costs in the cloud. The AWS Free Tier Dashboard shows the usage of each free tier.<br>
Cost Allocation Tags track AWS costs on a detailed level and groups them together. Tags are used to organize resources by creating groups. Both AWS generated tags and user-defined tags can be used. Tag Editor is used to manage the tags.<br>
We can generate AWS Cost and Usage Reports which will contain the most comprehensive set of AWS cost and usage data available. It lets you understand your bill and where charges are coming from.<br>
Cost Explorer allows visualization and management of AWS costs and usage over time. It indicates the optimal Savings Plan and can forecast usage up to 1 year based on past usage.

Billing Metric is stored in CloudWatch region us-east-1 and aggregates billing of all regions and thus indicates worldwide AWS costs. Billing Alarm can be used on top of Billing Metric to send an email notification when billing surpasses a certain treshold.<br>
AWS Budgets is more advanced and sends alarms when costs/usage or forecasted costs/usage exceed the budget. Different types of budgets can be created, Usage, Cost, Reservation and Savings Plan.

AWS Cost Anomaly Detection continuously monitors costs and usage using ML to detect unusual spends.

Quotas refer to limits. AWS services contain limits/quotas. AWS Service Quotas notify via CloudWatch Alarms when close to a service's quota value treshold. Before the limit is reached you can request a quota increase or shutdown of resources.

AWS Trusted Advisor gives a high level AWS account assessment. It will check certain things and advise on them to help provision resources. For example it will check if you have EBS public Snapshots/backups or RDS public Snapshots/backups or are you using the root account. To have a full set of checks you need a Business or Enterprise Support Plan which will also give you access to the AWS Support API.

Different AWS Support Plans exist.<br>
Basic Support Plan is free and gives access to 24x7 customer service, documentation and support forums. You also get access to AWS Personal Health Dashboard and 7 core AWS Trusted Advisor checks.<br>
AWS Developer Support Plan also provides business hours email access to Cloud Support Associates. Response times will depend on severity of problem.<br>
AWS Business Support Plan is intended to be used when having production workloads. It gives all Trusted Advisor checks and access to its API. It also provides 24x7 phone, email and chat access to Cloud Support Engineers. Response times are very short for production system impairments or downs. It provides architectural guidance in the context of client's specific use-cases.<br>
AWS Enterprise On-Ramp Support Plan is intended when having production or business critical workloads. It gives additionally access to a pool of Technical Account Managers (TAMs). For account and billing best practices next to operations reviews it gives access to the Concierge Support Team. Response times are even shorter with business-critical system downs being responded in 30min.<br>
The Enterprise Support Plan is intended when having mission critical workloads. It provides a designated TAM. Business-critical system downs are responded in 15min. It also gives access to online training with self-paced labs.<br>
Both the Business and Enterprise Support plans provide access to guidance, configuration, and troubleshooting of AWS interoperability with third-party software.

Credits in AWS can reduce charges related to a service. If EC2 charges $1000 and client has a credit of $100 for EC2, he will be able to lower his charges to $900. When having multiple credits, first those who expire the soonest need to be used, then those who are applicable to the least amount of products and lastly those who are oldest.

### Advanced Identity
AWS Security Token Service (STS) enables you to create temporary, limited-privileges credentials to access AWS resources.

Amazon Cognito provides identity for web/mobile application users. IAM users are for employees who need AWS access. Instead, web/mobile app clients can become a user in Cognito. Cognito manages web/mobile app users on AWS by creating a database of users.

Microsoft Active Directory (AD) is a database of objects such as user accounts, computers, printers, file shares, security groups and is found in on-premises not AWS.<br>
AWS does not have AD on it, however AD can be extended using AWS Directory Services.

AWS IAM Identity Center (successor to AWS Single Sign-On) gives a single sign-on, one login for all the accounts in an AWS organization. It basically provides one access to multiple AWS accounts and applications. It works by providing a screen with all accounts after login where you can choose with what account to continue.

### Other Services
Amazon Workspaces is a managed Desktop as a Service (DaaS) solution to easily provision Windows or Linux desktops. It eliminates the need for management of on-premise Virtual Desktop Infrastructure (VDI). If someone wants to have a Windows/Linux laptop in the cloud they can do so using Amazon Workspaces.

Amazon AppStream 2.0 is a desktop application streaming service. It allows streaming on any computer without provisioning infrastructure. The application is delivered from within a web browser.<br>
Amazon Workspaces provides a full VDI which can launch multiple applications, while with Amazon AppStream 2.0 one specific desktop application is streamed into a web browser.  

Internet of Things (IoT) is a network of internet-connected devices that can collect and transfer data. AWS IoT Core connects IoT devices to the AWS Cloud. It is serverless, secure and scalable.

AWS AppSync stores and synchronizes data across mobile and web apps in real-time. For this it leverages a technology from Facebook called GraphQL. To build this GraphQL backend, integration is possible with DynamoDB and Lambda.

AWS Amplify is a set of tools and services that help develop and deploy scalable full stack web and mobile applications. Amplify can manage authentication, storage, API, CI/CD, PubSub, analytics and ML, monitoring, source code from AWS or Github...

AWS Application Composer can be used to visually design and build serverless applications on AWS by generating CloudFormation infrastructure as code (IaC). It allows AWS infrastructure code deployment without being an expert in AWS.

AWS Device Farm is a managed service that tests your web and mobile apps against desktop browsers, real mobile devices and tablets.

AWS Backup is a managed service to centrally manage and automate backups across AWS services. It allows the creation of a backup plan where you define the frequency and retention policy of backups. This backup plan can be assigned to AWS resources such as EC2, EBS, RDS, DynamoDB... The backups are stored in S3.

Different disaster recovery strategies exist. Backup and Restore is the cheapest one. Pilot Light keeps the minimal critical functions of the app running in the cloud. Warm Standby is more expensive, it keeps the full app running in the cloud but at a minimum size. Multi-Site/Hot-Site is the most expensive, as it keeps the full app at full size running in the cloud.<br>
In the cloud we can perform disaster recovery of applications running in multiple regions, if one region fails we can failover the traffic to other region using route 53.

AWS Elastic Disaster Recovery (DRS) used to be named CloudEndure Disaster Recovery. It allows quick and easy recovery of physical, virtual and cloud-based servers into AWS.<br>
It performs continuous replication of servers into an AWS staging environment. Then in case of a disaster, the staging can be moved to production on which you can failover within minutes.

AWS DataSync moves large data amounts from on-premises to AWS by running an AWS DataSync Agent in on-premise. Replication/synchronization tasks can be scheduled hourly, daily, weekly. The replication tasks are incremental after the first full load.

7 cloud migration strategies exist:<br>
&nbsp;&nbsp;&nbsp;** Retire, is the first strategy that consists of deactivating services you don't need which reduces the surface area for attacks and saves costs.<br>
&nbsp;&nbsp;&nbsp;** Retain, consists of not migrating yet. Thus you retain the resources on-premises for reasons such as security, data compliance, performance or unresolved dependencies.<br>
&nbsp;&nbsp;&nbsp;** Relocate, moves app from on-premises to the cloud or move EC2 to a different VPC, AWS account or AWS region.<br>
&nbsp;&nbsp;&nbsp;** Rehost, is a simple migration that consists of re-hosting an application/database/data on AWS. Machines are migrated to AWS Cloud. AWS Application Migration Service allows to do that.<br>
&nbsp;&nbsp;&nbsp;** Replatform, consists of leveraging some cloud optimization without changing the core architecture. For example by migrating application to Elastic Beanstalk or database to RDS.<br>
&nbsp;&nbsp;&nbsp;** Repurchase, consists of moving to different product while moving to the cloud. Usually move to a SaaS platform. Expensive but fast.<br>
&nbsp;&nbsp;&nbsp;** Refactor / Re-architect, consists of changing application architecture using cloud native features. A monolithic application could be transformed to micro-services.

AWS Application Discovery Service plans migration projects by gathering information about on-premises data centers. It will gather server utilization data and map dependencies.<br>
The first type is Agentless Discovery which gives information around virtual machines, configurations and performance history. Agent-based Discovery gives more updates and information from within the virtual machines. Resulting data can be viewed within AWS Migration Hub.<br>
After collecting the data, AWS Application Migration Service (MGN) can be used to perform the migration. It works by running an AWS Replication Agent on any cloud to perform continuous replication into a staging environment in AWS Cloud, at one point staging can be moved to production which we call a cutover.

AWS Migration Evaluator provides a clear baseline of what own organization is running today to know workloads which is important information when wanting to migrate and form a migration plan. Agentless Collector needs to be installed on-premise to gather data, else data can be imported with other feature. This data is used to run the AWS Migration Evaluator which gives insights and indicates if migration is cost-effective to form a business case for migration to AWS.

AWS Migration Hub is a central location to collect servers' and applications' inventory data for the assessment, planning and tracking of migrations to AWS. This accelerates migration to AWS. It is integrated with services such as Application Migration Service and Database Migration Service.<br>
AWS Migration Hub Orchestrator is a sub-feature that provides pre-built templates to save time and effort migrating enterprise apps.

AWS Fault Injection Simulator (FIS) is a managed service for running fault injection experiments on AWS workloads. It is based on chaos engineering which refers to stressing an application via disruptive events to observe how it responds and implement improvements.

AWS Step Functions builds a serverless visual workflow to orchestrate Lambda functions. It also has some internal features such as sequencing, parallel functions, conditions, timeouts, error handling... Next to lambda functions, it also integrates with EC2, ECS, on-premises servers, API Gateways, SQS queues... The possibility also exists to implement a human approval step. Use cases are order fulfillment, data processing, web applications or any workflow.

AWS Ground Station is a managed service that allows control of satellite communications, process data, and scale own satellite operations. It allows satellite data downloads to AWS VPC within seconds. The use cases are weather forecasting, surface imaging, communications and video broadcasts.

Amazon Pinpoint is a scalable, inbound and outbound, marketing and communication service. It supports email, SMS, push notifications and in-app messaging. With it you can create campaigns using message templates, delivery schedules and targeted segments. Receiving replies is possible.

AWS OpsWorks is a configuration management service that provides managed instances of Chef and Puppet. Chef and Puppet are automation platforms that allow use of code to automate the configurations of servers. OpsWorks uses Chef and Puppet to automate how servers are configured, deployed, and managed across Amazon EC2 instances or on-premises compute environments.

### AWS Architecting and Ecosystem
Here we will cover the Well-Architected Framework which consists of advice on architecture.<br>
Good practice is to use auto-scaling instead of trying to guess capacity. Test systems at production scale. Automation can make architectural experimentation easier. Make architectural choices based on data.<br>
A design principle is for resources to be disposable, by having backups for example. Loose coupling is recommended and consists of using micro-services instead of a monolith. Think in services, not servers, avoid only using EC2, try to use managed services too.<br>
The six pillars of Well Architected Framework are, operational excellence, security, reliability, performance efficiency, cost optimization, sustainability.

Operational Excellence is the first pillar. It refers to the ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures.<br>
Use infrastructure/operations as code, which is an associated design principle. CloudFormation can be used for that. Also make small changes at a time so that if failure occurs they are reversible. Refine operations procedures frequently and ensure team members are familiar with it. Anticipate and learn from failure. Implement observability for actionable insights.

Security includes the ability to protect information, systems, and assets through risk assessments and mitigation strategies while delivering business value.<br>
As a design principle implement a strong identity foundation. Meaning, user account management should be centralized, reliance on long-term credentials should be reduced, IAM users should have least amount of privileges. Traceability should be enabled. Every layer should be secured, like edge network, VPC, subnet, load balancer, inctance, OS, application. Automate security best practices. Reduce direct access to data or need for manual data processing. Run incident response simulations and use tools to detect, investigate and recover.

Reliability is the ability of a system to recover from infrastructure or service disruptions, scale resources to meet demands, and mitigate disruptions such as misconfigurations or transient network issues.<br>
As design principle, test recovery procedures and automatically recover from failure. Scale horizontally to increase system availability. Use auto-scaling instead of guessing capacity.

Performance efficiency includes the ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve.<br>
As design principle, advanced technologies should be used. Going global should take minutes. Use serverless architecture to avoid the burden of managing servers. Be aware of all AWS services and don't be afraid to experiment.

Cost optimization includes the ability to run systems to deliver business value at the lowest price point.<br>
As design principle, pay only for what you use. Use CloudWatch to measure if resources are used effectively. Start using AWS to stop spending money on data center operations. Use tags to track costs of each application and analyze expenditures. Use managed services to lower costs.

Sustainability focuses on minimizing the environmental impacts of running cloud workloads.<br>
As design principle, understand own impact. Establish sustainability goals. Maximize the utilization of running services to be energy efficient. Adopt new hardware/software over time. Use managed services to share infrastructure. Reduce the amount of energy or resources required to use services and the need for cutomers to upgrade devices.

AWS Well-Architected Tool enables review of architecture in relation to the previously covered 6 pillars to adopt architectural best practices.

AWS Customer Carbon Footprint Tool is used to track, measure, review and forecast carbon emissions generated from AWS usage. Helps meet sustainability goals.

AWS Cloud Adoption Framework (CAF) is an ebook and not a service. It helps build and execute a comprehensive plan for digital transformation through innovative use of AWS. Thus how to transform by leveraging the cloud. It is based on best practices and lessons learned from 1000s of customers.<br>
CAF identifies organizational capabilities for successful cloud transformations. CAF groups its capabilities in 6 perspectives, Business, People, Governance, Platform, Security, and Operations.<br>
Within those 6 perspectives we can make distinction between Business capabilities which refer to the Business, People and Governance perspectives and the Technical capabilites which refer to Platform, Security and Operations perspectives.<br>
&nbsp;&nbsp;&nbsp;** The Business Perspective helps ensure that cloud investments accelerate own digital transformation ambitions and business outcomes.<br>
&nbsp;&nbsp;&nbsp;** The People Perspective serves as a bridge between technology and business. Via the people, focus is set on culture, organizational structure, leadership and workforce to help organizations evolve to a culture of continuous growth and learning.<br>
&nbsp;&nbsp;&nbsp;** The Governance Perspective helps orchestrate cloud initiatives while maximizing organizational benefits and minimizing transformation-related risks.<br>
&nbsp;&nbsp;&nbsp;** The Platform Perspective helps build an enterprise-grade, scalable, hybrid cloud platform to modernize existing workloads and implement new cloud-native solutions.<br>
&nbsp;&nbsp;&nbsp;** The Security Perspective helps achieve the confidentiality, integrity and availability of data and cloud workloads.<br>
&nbsp;&nbsp;&nbsp;** The Operations Perspective helps ensure cloud services are delivered at a level that meets own business needs.<br>
As Transformation Domains we have Technology, Process, Organization and Product, to help drive business outcomes.<br>
&nbsp;&nbsp;&nbsp;** Technology refers to using the cloud to migrate and modernize legacy infrastructure, applications, data and analytics platforms.<br>
&nbsp;&nbsp;&nbsp;** Process refers to digitizing, automating and optimizing own business operations. Leveraging data and ML.<br>
&nbsp;&nbsp;&nbsp;** Organization refers to reimagining operating model. By re-organizing teams and using methods to rapidly iterate and evolve.<br>
&nbsp;&nbsp;&nbsp;** Product refers to reimagining own business model by creating new value propositions (products/services) and revenue models.<br>
CAF has 4 Tranformation Phases.<br>
&nbsp;&nbsp;&nbsp;** Envision is the first Transformation Phase. It demonstrates how the cloud will accelerate business outcomes by identifying transformation opportunities and create a foundation for own digital transformation.<br>
&nbsp;&nbsp;&nbsp;** Align identifies capability gaps within the 6 CAF Perspectives which results in an action plan.<br>
&nbsp;&nbsp;&nbsp;** Launch builds and delivers pilot initiatives in production and demonstrates incremental business value.<br>
&nbsp;&nbsp;&nbsp;** Scale expands the pilot initiatives.

Right sizing is the process of matching instance types and sizes to your workload performance and capacity requirements at the lowest possible cost. Because scaling is easy in the cloud it is best to always start small.<br>
After instances are deployed it is possible to continuously look at opportunities to eliminate or downsize them by evaluating usage metrics which would lower costs.

A lot of services exist in the AWS Ecosystem.<br>
A lot of resources are free such as AWS Blogs, AWS Forums, AWS Whitepapers and Guides. The Well-Architected Framework is an example of a whitepaper. AWS Partner Solutions (formerly Quick Starts references) is also free and provides automated, gold-standard deployments in the AWS Cloud by leveraging CloudFormation templates. An example is Wordpress on AWS. AWS Solutions is also free and a way to deploy popular technology solutions to the AWS Cloud.<br>
Different AWS Support Plans, such as Developer, Business and Enterprise, as covered previously, are part of the AWS Ecosystem.<br>
The AWS Marketplace is a digital catalog with thousands of software listings from independent (third party) software vendors. For example you can buy a custom AMI, CloudFormation template or SaaS. Own solutions can also be sold on AWS Marketplace.<br>
AWS Training can be digital (online) or from a classroom (in-person or virtual). AWS Private Training exists for an organization. Dedicated training and certification programs for the US government or an enterprise also exist. AWS Academy exists to help universities teach AWS.<br>
The AWS Professional Services organization is a global team of experts in AWS that help clients by working alongside own team and a chosen member of the AWS Partner Network (APN). APN is a network of people that AWS knows are good in cloud. The APN Technology Partners provide hardware, connectivity and software. While the APN Consulting Partners help migrate, build and manage on AWS. The APN Training Partners help own team learn AWS. The AWS Competency Program is granted to APN Partners who demonstrated technical proficiency and customer success in specialized solution areas. Lastly, the AWS Navigate Program trains Partners to become better Partners.

AWS IQ is used to quickly find and pay a professional to help own AWS projects. Those professionals are third party, AWS certified experts. AWS IQ also provides video-conferencing, contract management, secure collaboration and integrated billing. The client must submit a request on the platform and review responses to select an expert to work with afterwards. Charges are added to AWS bill.<br>
Alternatively AWS re:Post can be used, which is a community forum where you can find answers. Thus it is an AWS managed Q&A service offering crowd-sourced, expert-reviewed answers to technical questions about AWS. It replaces what used to be the original AWS Forums. Questions from AWS Premium Support customers that do not receive a response from the community are passed on to AWS Support engineers.<br>
AWS Knowledge Center is part of re:Post. It is a place to find the most common questions on AWS.

AWS Managed Services (AMS) consists of a team of AWS experts who provide infrastructure and application support on AWS. They manage and operate client's infrastructure for security, reliability and availability. 

## Udemy course - AWS certified machine learning specialty
This certification is different compared to other certifications in that half of the learned knowledge is not related to AWS but instead to general machine learning knowledge. The other half is related to AWS and more specifically its service SageMaker.

### Data Engineering
Data needs to be stored in a way that allows use by machine-learning (ML) models, scaling and security.

S3 allows storage of objects/files inside buckets/directories.<br>
Each bucket must have a globally unique name. What we call objects are files who have a key. This key is the path of the file.<br>
The object value is the content of file body which can be everything you want but has a size limit of 5TB, if larger than that you must use 'multi-part upload'.<br>
Object tags are used to classify/partition data and for security. They consist of key-value pairs.<br>
S3 is often used as data storage for AWS ML services such as SageMaker. It can be used to create a 'data lake'. A 'data lake' is a centralized repository designed to store large amounts of data. Here, S3, demands no provisioning, can have infinite size, has 99.999999999...% durability. It also allows decoupling storage from compute to manage costs of storage and compute separately.<br>
Data partioning allows speeding up queries by classifying data via date for example. Certain tools such as Kinesis or Glue can partition data for us.

S3 has different storage classes. What differentiates them is that the more expensive ones return your stored data faster and/or more often.
It is possible to move between them manually or using S3 Lifecycle configurations.
Durability indicates how often data is lost and is similar between storage classes. Availability indicates how readily available a service is which in AWS usually is 99.99%.
The Standard storage class is general purpose.
The Infrequent Access storage class is for data that is less frequently accessed but when needed requires rapid access. It is cheaper than Standard storage class. One-Zone Infrequent Access is cheaper than Standard Infrequent Access.
The Glacier storage class is low cost and meant for archiving/backup. You pay for storage and object retrieval. It has the 'Instant Retrieval' option and 'Flexible Retrieval' option with different retrieval time options of 5min to 12hours.
S3 Glacier Deep Archive is Amazon S3’s lowest-cost storage class and supports long-term storage for data that may be accessed once or twice in a year. It is designed for customers in highly-regulated industries, such as the Financial Services, Healthcare, and Public Sectors, that retain data sets for 7-10 years or longer to meet regulatory compliance requirements. S3 Glacier Deep Archive can also be used for backup and disaster recovery use cases. It has a retrieval time of 12 to 48 hours.
The last storage class is Intelligent-Tiering which allows you to automatically move between storage classes based on usage.

S3 Lifecycle rules can be created to automatically move S3 objects between storage classes or delete them. For example you can create 'transition actions' which are rules that move objects to another storage class after some time. Else, 'expiration actions' are rules that delete objects after some time or delete old versions when using versioning.

IAM policies can be used for security in S3 by determining accessibility of users towards buckets. Bucket policies determine accessibility of the bucket towards users but can also enforce encryption. Those policies are written in JSON. <br>
Lastly, for security on S3, object encryption can be used.

* Four methods exist in S3 for encryption:
  * Server-side encryption (SSE)
    * SSE with Amazon S3-Managed Keys (SSE-S3) uses keys handled, managed and owned by AWS.
      * It is enabled by default. Encryption type is AES-256.
    * SSE with KMS Keys stored in AWS (SSE-KMS) leverages AWS Key Management Service (KMS) to manage encryption keys.
      * KMS allows user control and logging in CloudTrail. Its disadvantage is the need for API calls to KMS when encrypting and decrypting.
    * SSE with customer provided keys (SSE-C) when wanting to manage own encryption keys.
      * AWS does not store the client provided encryption keys. 
  * Cliend-side encryption when encryption is done before upload to S3.
    * Encryption/decryption is fully managed by the client outside of S3. The 'Amazon S3 client-side encryption library' can be used.<br>
* Encryption in transit/flight (SSL/TLS) refers to the HTTPS endpoint of S3 which encrypts in transit. S3 has both HTTP and HTTPS endpoints but the HTTPS endpoint is recommended as it has encryption in flight. For SSE-C HTTPS is mandatory. Encryption in transit can be forced using a bucket policy.

Usually the public internet is used to access S3 via a public subnet that connects via an Internet Gateway. A private subnet can be used to keep S3 instance private via a VPC Endpoint Gateway.

AWS Kinesis is a streaming service and managed alternative to a technology called 'Apache Kafka'. It is great for 'real-time' big data and gathering application logs, metrics, IoT device information, clickstream data.<br>
Kinesis holds four services. 'Kinesis Streams' ingests low latency streaming data at scale. 'Kinesis Analytics' performs real-time analytics on streams using SQL. 'Kinesis Firehose' loads data into S3, Redshift and ElasticSearch, but also to third-party partners such as Splunk or even custom destinations. 'Kinesis Video Streams' is meant for streaming video in real-time.<br>
Here is an example workflow were streaming data is gathered using 'Kinesis Streams', real-time analytics are performed on this data using 'Kinesis Analytics', and finally we use 'Kinesis Firehose' to distribute the streaming data in S3 and Redshift.<br>
![Screen Shot 2024-06-20 at 15 17 39](https://github.com/artainmo/DevOps/assets/53705599/06e62e43-4261-4718-834c-59937b9ca24c)<br>
Streams can be viewed as being composed of shards/partitions. The maximum throughput of a single chard is 1 MB/s or 1000 messages/s. In 'Kinesis Streams' data retention is 24h by default but can be set to 365 days. If usage capacity is not known in advance, use on-demand mode, else provision mode is cheaper.<br>
'Kinesis Analytics' will take data from 'Kinesis Data Streams' or 'Kinesis Data Firehose', perform SQL queries on that data and send the result back to 'Kinesis Data Streams' or 'Kinesis Data Firehose'. When performing ML on 'Kinesis Data Analytics' two algorithms can be used, namely 'random cut forest' which is used for anomaly detection on numeric columns in a stream thus it finds outliers in data, and 'hotspots' which returns information about dense regions in data. 'Kinesis Data Analytics' can also be used to perform real-time extract, transform and load (ETL).<br>
Lambda can be used for pre-processing or post-processing the data before or after using it in 'Kinesis Data Analytics'. Post-processing it can be used to aggregate rows, translate to different formats, transform/enrich the data, encrypt, and send it to other destinations such as Aurora or SNS or CloudWatch.<br>
Each video stream with 'Kinesis Video Stream' has one producer. A producer can be any camera type. DeepLens is a camera by Amazon. 'Kinesis Video Stream' has video playback capability. Those streams can be consumed by other services such as Amazon Rekognition or SageMaker. Thus 'Kinesis Video Stream' connects video producers to the AWS cloud for further processing. Stream data can be kept for 1 hour to 10 years.

AWS Glue Data Catalog is a central repository to store metadata for all your tables. It can for example index all datasets within amazon S3. It integrates with Athena or Redshift for data discovery. Data discovery is the process of visually navigating data and applying advanced analytics in order to detect patterns, gain insight, or answer specific questions.<br>
Glue Crawlers help build the Glue Data Catalog. They go through data and infer shemas and partitions.<br>
Glue ETL stands for extract transform load and is a service that transforms, cleans, enriches data, before doing analysis. Its runs on a serverless Apache Spark platform. It can also perform ML transformations with 'FindMatches ML' to identify duplicate or matching records in dataset.<br>
AWS Glue DataBrew allows cleaning and normalizing data without writing any code.

Amazon Relational Database Service (RDS) is a managed service for the use of a SQL database in the cloud. Amazon Aurora is a database technology who supports PostgreSQL and MySQL, because it is cloud optimized, performances on PostgreSQL and MySQL is more efficient. It is more expensive than RDS but more efficient. Aurora is serverless and managed by RDS.<br>
Redshift is a database type based on PostgreSQL designed for large scale data set storage and analysis. It acts as a data warehouse which is a central repository containing data from one or more disparate sources. It is not used for online transaction processing (OLTP), which is what RDS is good for. Instead Redshift is used for online analytical processing (OLAP). Usually S3 data needs to be loaded into Redshift to perform its SQL queries, however, Redshift Spectrum can be used to query directly into S3. While Redshift can perform analytics, RDS and Aurora only store data.<br>
DynamoDB is a serverless NoSQL database while S3 stores objects.<br>
OpenSearch (previously called ElasticSearch) is used to index data and search among data points, but also for clickstream analytics.<br>
ElastiCache has a caching mechanism which allows faster data retrieval, thus lower latency.

AWS Data Pipeline moves data from one place to another. It can retry and notify on failure. It also handles data on-premises. It acts as an orchestrator that creates EC2 or EMR instances to perform the actual data ETL.

AWS Batch is a scalable and managed batch processing service. It can run 100,000s of computing batch jobs on AWS. A batch job is a job with a start and end, thus it is not continuous. Batch jobs are defined as Docker images and run on ECS.<br>
Lambda and Batch both execute functions/jobs. They differ in that Lambda has a time and disk space limit while batch has no such limits. However, Lambda is serverless while Batch relies on EC2.<br>
AWS Batch can be used to perform ETL jobs. However, Glue ETL would be better for such tasks.

Database migration service (DMS) is a service that migrates data from one database (DB) to another. DMS runs in an EC2 instance, extracts datas from the source DB and inserts it in the target database. It performs continuous data replication using change data capture (CDC) thus it migrates in real-time.

AWS Step Functions is used to design and orchestrate a visual workflow. The ability to wait between steps exists, and a workflow can have a maximum execution time of one year. The possibility exist to audit history and retry steps after failure. Step Functions can be used to train a machine learning model for example.

AWS DataSync moves large data amounts from on-premises to AWS.<br>
In the case of ML, IoT uses physical devices/sensors to feed data in a centralized repository to be used by ML model. MQTT is an internet of things (IoT) standard messaging protocol. Thus it helps transfer sensor data to ML model.

### Exploratory Data Analysis
This section is about pre-processing the data that will be used by our ML model.

Python is the programming language of choice in ML and data science. Pandas is a library that uses DataFrames, which is a table that holds values, to manipulate data. A Series is a one-dimensional row from a DataFrame. It interoperates with Numpy. Numpy performs operations on multi-dimensional data in pyton and often is the data format used by actual ML algorithms.<br>
Matplotlib allows visualization of data from Pandas DataFrames or Numpy arrays. It can be useful to visualize data distributions and outliers. Seaborn produces even more advanced plots. It contains heatmaps which represent data in part via colors indicating the average value at each point.<br>
Scikit-learn is the python library for ML models.

The main data types are numerical, categorical and ordinal.<br>
Numerical data represents a quantitative measurement.<br>
Categorical data has no inherent mathematical meaning even if you can use numbers to represent/differentiate the categories.<br>
Ordinal data is a mixture of numerical and categorical data. An example is star ratings for a restaurant. One to five stars are possible and represent categories and those categories have mathematical meaning.

Data distributions represent the likelihood of data falling into a certain range.<br>
A normal distribution is a bell curve centered around a central value. A normal distribution is an example of a probability density function and is used for numerical data.<br>
![Screen Shot 2024-06-21 at 14 22 22](https://github.com/artainmo/DevOps/assets/53705599/48649c67-5fb8-4db2-88f2-f548f2f496d7)<br>
Data that can only take certain values is called discrete data or discrete values. This is data that can be counted and has a limited number of values. It usually comes in the form of whole numbers or integers. When using discrete data we use probability mass functions instead which look like histograms and uses single values instead of ranges. Poisson distribution is an example.<br>
![Screen Shot 2024-06-21 at 14 24 01](https://github.com/artainmo/DevOps/assets/53705599/e695384b-1d3d-412c-86a7-3497dc0a19ab)<br>
Binomial distributions are used for binary classifications of discrete events, such as flipping a coin.

Time series are a series of data points over time. Noice refers to random variations in time series data.

Athena is a serverless SQL query service for S3. Under the hood it is powered by Presto. It can be used to query and analyze logs. It integrates with a lot of other services. AWS Glue can create a shema and transform data which can be useful for Athena. Amazon Quicksight can then be used to visualize the Athena queries. With Athena you pay-as-you-go, $5 per scanned TB. Converting data to columnar formats (such as ORC or Parquet) saves a lot of money because it allows Athena to be selective in the columns it needs to read.

Amazon QuickSight is an analytics and visualization tool. It allows quick creation of dashboards, graphs and reports. It is aimed more towards end users as an application and less towards developers. Under the hood it uses Super-fast, Parallel, In-memory, Calculation Engine (SPICE). It is used for interactive exploration/visualization of data, dashboards and KPI reports.<br>
It contains a feature called 'Machine Learning Insights' which can perform anomaly detection, forecasting and auto-narratives to automatically build dashboards using ML.<br>
QuickSight Q is a ML powered add-on to QuickSight which answers plain language questions about the data using NLP. The datasets need to be NLP friendly and personal training is necessary on how to use it.<br>
Another feature is Quicksight Paginated Reports which produces printable reports for management.<br>
QuickSight is best not used for highly formatted canned reports. Unless when using QuickSight Paginated Reports, but the exam may not be updated on this new nuance.<br>

* Different visual types exist in QuickSight:
  * AutoGraph automatically selects the most appropriate visualization based on the properties of the data.
  * Bar charts such as histograms can be used for comparisons between data and distributions of data.
  * Line graphs can be used for visualizing changes over time.
  * Scatter plots and heat maps for correlation between data.
  * Pie graphs and tree maps for aggregation indicating where most of the data lies.
  * Pivot tables for tabular thus multi-dimensional data on which we can perform statistical functions.
  * Donut charts show a percentage of a total amount. This is best when precision is not important and only a few items exist in a dimension.
  * Gauge charts indicate the value of a measure. It looks like the gauge used to indicate fuel in a tank.
  * KPIs are used to compare key value to its target value.
  * Geospatial charts show data over a map.
  * Word clouds show the frequency of words or phrases in a dataset.
  * Box and whisker plots organize data into quartiles, and display outliers in the outer quartiles.

Elastic MapReduce (EMR) helps create Hadoop clusters to analyze and process vast amounts of data. Those clusters can be made of 100s of EC2 instances with each cluster being called a node. Each node has a role and type. The master/leader node manages the cluster and distributes the data across the other nodes. Core nodes run tasks and store data on the Hadoop Distributive File System (HDFS). Task nodes only run tasks, are not mandatory and don't store data. As a result they are good for spot instances who are not reliable.<br>
For massive datasets you sometimes need a cluster to process it in parallel.<br>
HDFS is fast but data is lost when cluster is shut down. EMRFS can use S3 as if it was HDFS to avoid this problem.<br>
A transient cluster terminates after the defined steps/tasks are all completed while long-running clusters need to be manually terminated.<br>
It can integrate with EC2, Amazon VPC, S3, IAM, CloudTrail, Data Pipeline.<br>
EMR Notebooks is similar to Jupyter Notebooks. It runs on an EMR cluster and has several integration points with AWS services.<br>
EMR charges by the hour plus the associated usage of EC2 costs too.

Hadoop consists of MapReduce, YARN and HDFS.<br>
YARN stands for Yet Another Resource Negatiator. It centrally manages cluster resources.<br>
MapReduce is a software framework to easily write applications that process vast amounts of data in parallel on large clusters. However, lately, Apache Spark has largely replaced MapReduce as it is faster due to caching and optimized query execution by using a directed acyclic graph.<br>
Spark has multiple components. Spark Core acts as the foundation of the platform and is responsible for memory management, fault recovery, scheduling and distributing jobs, and interacting with storage systems. It uses a resilient distributed dataset (RDD) to collect data partitioned across different compute nodes.<br>
Spark SQL is a distributed query engine that provides low latency interactive queries up to 100 times faster than MapReduce.<br>
Spark Streaming performs streaming analytics. It uses a growing table to store data over time which can be queried in relation to the time. It integrates with Kinesis.<br>
The ML library for Spark is called MLLib. MLLib offers several ML algorithms who are implemented in a distributed and scalable way by leveraging the cluster and parallel computing.<br>
GraphX is a distributed graph processing framework in Spark, it provides ETL and exploratory analysis.<br>
Zeppelin is a notebook to run Spark code and for example execute SQL queries directly against SparkSQL and visualize the results in charts and graphs. EMR Notebook is similar to Zeppelin but with more AWS integration.<br>
Kerberos is used for security of EMRs. It provides strong authentification via key cryptography. Apache ranger can integrate with EMR for data security.<br>
The master node can use as Instance Type an m4.large if having less than 50 nodes, else an m4.xlarge. For core and task nodes m4.large is in general good too. For AI and accelerated computing you may want GPU instances. Spot instances are usually a good choice for task nodes.

Feature engineering is the process of selecting what features in the data are important for ML models to predict. You may also need to transform the selected data, handle missing data, or even create new features from existing ones.<br>
Too many features can be problematic by leading to scattered data which is called 'the curse of dimensionality' and is why we need to select the most important features or use unsupervised dimensionality reduction algorithms such as PCA or K-means to distill many features into less features.

Mean replacement is one solution for missing data. If a data misses replace it with the mean of the entire feature column. If data has a lot of outliers you may prefer to use the median instead of mean. If the data is categorical you cannot use this method but instead should use the most frequent value. However, the mean replacement method is usually not very accurate.<br>
An alternative, which neither is best solution, is to drop the missing rows.<br>
ML can be used to impute missing data which may be best solution. KNN can be used to find average of N most similar rows. It does not work for categorical data. Deep Learning can be used to impute data, also categorical data. Or regressions can be used with MICE (Multiple Imputation by Chained Equations) being such an advanced technique.<br>
Lastly, collecting more real data is another way to combat missing datas.

Unbalanced data refers to having a large discrepancy between positive and negative cases. For example fraud is rare and the associated dataset will contain way more negative cases. This is especially a problem with neural-network who will have too few positive training cases and as a result always predict negative.<br>
One solution is 'oversampling' where minority class samples are duplicated at random. Inversely, 'undersampling' consists of removing majority class samples, however, eliminating data is usually undesirable besides when having scaling issues.<br>
Synthetic Minority Over-sampling Technique (SMOTE) is even better than 'oversampling' and 'undersampling'. It creates new samples of the minority class by using KNN on each minority sample.<br>
With neural-networks a final score is given at output, a treshold is used to predict if this score indicates one class or the other. Adjusting this treshold to predict the minority class more often could help.

Variance (σ<sup>2</sup>) is the average of the squared differences from the mean. Standard deviation (σ) is the square root of the variance. An outlier is at least one or two standard deviations away from the mean.<br>
Sometimes it is best to remove outliers other times not. The AWS Random Cut Forest algorithm can be used for outlier detection.

Binning is transforming ranges of numerical values into categorical values. Binning covers up imprecisions in measurements. With quantile binning data is categorized relative to its distribution thus it ensures each bin has an equal amount of samples.<br>
Data can be transformed to make it more suitable for training. For example exponential data may benefit from a logarithmic transform to make it more linear.<br>
Sometimes data needs to be encoded in a format required by the ML model. An example is one-hot-encoding where a category gets transformed into a string of 0-1 values, where all categories equal zero besides the category being represented has value 1.<br>
Some ML models prefer data to be normally distributed which demands data normalization. Data of one feature can also be scaled to values comparable to other features. All features should be on same scale to avoid some having more weight than others.<br>
Shuffling can also benefit many ML algorithms by not making data order predictable.

SageMaker Ground Truth manages humans to label your data for training purposes. For example if you have a lot of pictures and need labels on them, humans may be the only way to label them. Ground Truth will also learn on the way and only ask humans to label data he cannot predict with certainty. Ground Truth Plus is even simpler to use as it lets AWS Experts manage the whole workflow and team of labelers.<br>
Instead of using humans to label images or text, one can also use AWS Rekognition or Comprehend respectively. Any pre-trained model or unsupervised technique may be helpful for labeling.

Term Frequency and Inverse Document Frequency (TF-IDF) is used in search algorithms to find how relevant a given term is for a given document.<br>
Term Frequency (TF) measures how often a word occurs in a document while Document Frequency (DF) is how often a word occurs in an entire set of documents which indicates what words are common among any document/topic and thus are not relevant. So to measure the relevancy of a word to a document we divide TF by DF. We can also measure n-grams instead of only individual words.

### General Deep Learning and Machine Learning
Parallelization is useful for neural networks. GPUs (graphics processing unit) use parallelization to make all the screen pixels appear simultaneously. But GPUs can also be used for parallelization with neural networks.

A popular framework for deep learning is tensorflow which contains a higher-level API called Keras. Apache MXNet is also a deep learning framework. Amazon's deep learning services are often build on MXNet.

* Different neural network types exist:
  * Feedforward neural network is the most basic one.
  * Convolutional neural networks (CNN) are often used for image recognition because they handle two-dimensional data.
  * Recurrent neural networks (RNN) deal with sequences such as sequences of time when predicting stock prices or with sequences of words in NLP. LSTM and GRU are different types of RNN.

* An activation function defines the output of a node/neuron given its input signals.
  * The simplest activation function is the linear activation function. This simply outputs what it got in input. They are not useful in deep learning.
  * A binary step function returns 0 if input is negative, else 1 and thus can only be used for binary classification.
  * Alternatively non-linear activation functions can create complex mappings between inputs and outputs. This allows for multiple layers and backpropagation, thus deep learning.
    * Sigmoid activation function also known as logistic activation function outputs values between 0 and 1.
    * TanH or hyperbolic tangent outputs values between -1 to 1. It is generally preferred over sigmoid.
    * Rectified Linear Unit (ReLU) outputs 0 when input is negative, else the input value itself. It is very fast to compute while Sigmoid and TanH are more computationally expensive. Sigmoid and TanH are more susceptible to the '[vanishing gradients problem](https://github.com/artainmo/machine-learning/tree/main/supervised-learning%20and%20neural-networks#Vanishing-gradient-problem)' when input values are small. But ReLu is susceptible to the 'dying ReLU problem' when inputs are zero or negative.
      * The solution to the 'dying ReLU problem' is Leaky ReLu. Which outputs smaller negative value when input is negative instead of 0. The extend to which the value is smaller can be calculated using backpropagation which we call Parametric ReLU (PReLU). However this is computationally expensive.
      * Another variant of ReLU is Exponential Linear Unit (ELU) where exponentially smaller negative values are given as output when input is negative.
      * A variant of ReLU that works well on deep learning models with 40 or more layers is Swish.
      * A last ReLU variant is Maxout which outputs the maximal value of all inputs. It is more computationally expensive and usually not worth using.
    * Softmax is an activation function usually used in the final output layer of a classification problem. It converts outputs from last layer into probabilities for each classification.
* How to choose an activation function:
  * For multiple classification use softmax on output layer.
  * For RNNs use TanH.
  * Use Swish for very deep (40+ layers) neural networks.
  * Else start with ReLU.
    * And if not good enough try Leaky ReLU, PReLU or Maxout.

CNNs are 'feature-location invariant' which means they find features that are not in an expected specific spot. Like a stop sign in a picture or words in a sentence. Thus they are used in image recognition or NLP.<br>
CNNs are inspired by the biology of our visual cortex. Local receptive fields are groups of neurons that only respond to a part of what our eyes see. They subsample the image coming from the retinas and overlap each other to cover the entire visual field which we call convolution. Thus by convolution we mean it breaks up data in chunks and processes those chunks individually. Later the system assembles a bigger picture of what is being seen. In CNNs multiple layers are used. A hierarchy exists of layers that first identify lines and edges, then shapes from those lines, and finally objects from shapes. For color images, additional layers are necessary for red, green, blue, those too are processed individually and assembled later.<br>
CNNs are computationally expensive. They contain a lot of hyperparameters. Specialized CNN architectures define hyperparameters for you. For example LeNet-5 is good for handwriting recognition. AlexNet is deeper and used for image classification. GoogLeNet and ResNet are even deeper and have better performance. AWS and SageMaker often use ResNet and variations of it like ResNet-50.

RNNs are for sequences of data, such as time or word sequences. It can be used for machine translation, image captions, machine-generated music, predict stock trades, predict car trajectory based on past trajectories.<br>
It has a neuron for each time step. The first neuron receives first data input in time and sends output to second neuron who also takes second data input and sends output to third neuron who also takes third data input, and so forth... Thus RNNs use current and past data. However recent information tends to influence the current time step more. This can be a problem but some solutions exist such as using Long Short-Term Memory (LSTM) cells and Gated Recurrent Unit (GRU) cells. GRUs are simpler than LSTMs while they perform almost as well.<br>
RNNs can be 'sequence to sequence' meaning they take and output a sequence as when predicting stock prices from historical data. Or they can be 'sequence to vector' as when predicting a sentiment from words. Or vector to sequence as when creating captions from images. In machine translation we will 'encode' by transforming a sequence into a vector and subsequently 'decode' by transforming the vector into a sequence.<br>
Backpropagation needs to be applied to each time step. This can look like a very deep neural network being computationally expensive. As a result truncated backpropagation is used where we limit backpropagation on a limited number of time steps.<br>
RNNs are sensitive to its hyperparameters and resource intensive, thus they are difficult to train.

Transformer deep learning architectures are the current state of the art in NLP. It uses a mechanism we call self-attention where each part of the input data is weighted on significance. One difference with RNNs is that it can process all time steps in parallel. The attention mechanism provides a context around each word to process them all in parallel.<br>
Examples of models built on the transformer architecture are Bi-directional Encoder Representations from Transformers (BERT), RoBERTa, T5, Generative Pre-trained Transformer (GPT)-2, GPT-3. DistilBERT too and it uses knowledge distillation to reduce model size by 40%.<br>
Because NLP models (LLM) are huge they are expensive to train. This is why pre-trained models such as 'Hugging Face' are used as a starting point. Hugging Face is a giant repository of pre-trained models everyone can use for free. They have a lot of transformer models as well such as GPT2 and Llama. Hugging Face via deep learning containers integrate with SageMaker. Using a Hugging Face deep learning container (DLC) in SageMaker we can import a BERT model that has been pre-trained on BookCorpus and Wikipedia. Such a pre-trained model you can fine-tune with own training data using transfer learning. For that you need to tokenize your training data and use it for further training of the model using a low learning rate to not eliminate previous learnings. Another way of transfer learning is to add new trainable layers to the top of a frozen model.

EMR supports MXNet, TensorFlow and PyTorch and GPU instance types to accelerate those. Different instance types can be used for deep learning on EMR or EC2, they are all Nvidia chips, for example P3 is more expensive, P2, G2 and P4d which can form UltraClusters by pairing multiple P4ds together. G5g paired with T4G are available on EC2 but not EMR and also used for Android game streaming. Also you can use AMIs configured for deep learning on EC2 instances. Else, SageMaker allows automatic deployment of desired architecture. As a reaction to the rise in generative AI, Amazon launched in 2023 other instance types, such as Trn1 which is optimized for training large neural networks. Trn1n instances are even faster. Inf2 instances are optimized for using pre-trained models.

Gradient descend is the main mathematical algorithm behind neural-networks. It tries to go down a cost function by changing neural-network weights and biases to minimize the cost which refers to degree of prediction errors. The learning rate refers to the step size used when performing gradient descend and is a hyperparameter. A small learning rate leads to slowly going down the cost function while a high learning rate comes with risk of missing global minima of cost function.<br>
Another important hyperparameter is the batch size which indicates how much training samples are used within each batch of each epoch. Smaller batch sizes can help exit local minimas because they introduce more noise into the gradient. Thus large batch sizes can converge on different solutions with different accuracy each time you train them due to getting stuck in random local minimas.

Regularization are techniques intended to prevent overfitting. Overfitting refers to a model that performs very well on its training data but not on never seen data.<br>
A simple regularization method is to simplify the model by reducing layers or neurons so that it won't overfit on training data and instead generalize more.<br>
The dropout method is another regularization technique. It works by temporarily removing (dropping out) certain nodes and all its associated connexions. This forces all nodes to learn which prevents one dominant node from overfitting.<br>
The early stopping method tests model against a validation dataset while training and stops training when the validation dataset starts to indicate overfitting.
L1 and L2 regularization adds a regularization term as weights are learned. L1 refers to sum of weights and L2 to sum of square of weights. L1 can be useful in the case of 'curse of dimensionality' but else if all features are of importance L2 would be preferred.

When the slope of the cost function approaches zero, the ML model ends up working with small values that slow down training and can even cause numerical errors. This is called the vanishing gradient problem. In deeper networks and RNN these vanishing gradients can propagate to deeper layers. The opposite problem is called exploding gradients and can also lead to numerical errors.<br>
Multiple solutions exist to the vanishing gradient problem. One of them is to use a multi-level hierarchy which consists of splitting neural network into several layers who are trained individually. LSTMs and ResNet can also prevent vanishing gradients. ReLU is the best activation function to prevent vanishing gradients.<br>
Gradient checking is a debugging technique that verifies the correctness of the computed derivatives. It is used to validate the neural network training code.

Accuracy is used to evaluate a ML model's performance by giving the percentage of correct responses. Sometimes we need to understand more, namely true positives, true negatives, false positives and false negatives. A confusion matrix can show this. A confusion matrix can show how much predictions were made of a certain class while the answer is a certain class. It can also indicate accuracy and [F1 score](https://github.com/artainmo/machine-learning/tree/main/supervised-learning%20and%20neural-networks#evaluation) relative to a class. It can look like in the following image.<br>
![Screen Shot 2024-06-23 at 19 51 30](https://github.com/artainmo/DevOps/assets/53705599/12fab3f5-6e0b-42ce-84b6-246c3a671c99)<br>
Recall is another measure to evaluate a ML model's performance. It is calculated by dividing the true positives by the true positives added to the false negatives. It gives the percentage of true positives. It is also called Sensitivity, True Positive rate, and Completeness.<br>
Precision or Correct Positives is calculated by dividing true positives by true positives added to false positives. It is a good metric choice when caring about false positives.<br>
Specificity, also called true negative rate, is another metric and is calculated by dividing true negatives with true negatives added to false positives.<br>
[F1 score](https://github.com/artainmo/machine-learning/tree/main/supervised-learning%20and%20neural-networks#evaluation) is a metric often used that provides a harmonic mean of precision and recall and is used when both false positives and true positives matter. It is calculated by multiplying 2 with precision times recall and to divide the result by precision added to recall.<br>
Root mean squared error (RMSE) measures accuracy thus it only cares about right and wrong answers.<br>
The Receiver Operating Characteristic (ROC) Curve plots the recall (true positive rate) vs false positive rate. The more the plotted curve bends towards the upper-left, the better. The area under the curve (AUC) can be used as a metric where 0.5 is as good as random and 1.0 is perfect. It is useful to compare classifiers.<br>
The Precision / Recall (P-R) Curve plots the recall and precision metrics. Again, the higher the AUC the better. It is similar to ROC but better for information retrieval as it is more readable as values are less small.

An ensemble method takes multiple models, which may just be variations of the same model, and lets them all vote on a final result. Random forests is one example of an ensemble method that combines the result of multiple decision trees to reach a single result. Using multiple decision trees like that often ends up with better results compared to only using one decision tree.<br>
Bagging generates multiple training sets by random sampling. Each training set can be used on a different model that can run in parallel.<br>
With boosting we assign weights to each observation in our dataset. This runs in a sequential manner where we start with equal weights on each observation, and at each stage reweigh the data and the model. We keep iterating to get better results. By weighing the data we increase or decrease the scale of certain features to give them more or less influence on the model being trained.<br>
XGBoost is part of SageMaker to perform boosting and is an often used algorithm. A lot of Kaggle challenges are being won by XGBoost right now, its strength is accuracy. On the other hand bagging is useful for overfitting as it spreads and subsamples the data. Also bagging can be parallelized.

### Amazon SageMaker
SageMaker is intended to manage the entire ML workflow. SageMaker's architecture looks like this.<br>
![Screen Shot 2024-06-24 at 12 58 42](https://github.com/artainmo/DevOps/assets/53705599/9c69965e-425d-45d3-a0e7-7ded76eb69c5)<br>
Data is expected to come from S3. Its ideal format varies with algorithm, often RecordIO or Protobuf. But data can also come from Athena, EMR, Redshift, and Amazon Keyspaces DB. SageMaker will provision training hosts to perform the data processing and training using that data. The code behind the model itself comes from a Docker image registered in Elastic Container Registry (ECR). The trained model and any artifacts will subsequently be stored in S3. For deployment in production we will use another Docker image from ECR with inference code thus code for model to predict. This is used inside hosts with endpoints provided by SageMaker again. When deploying, persistent endpoints can be used to answer individual requests on demand or SageMaker Batch Transform can be used to predict an entire dataset once. SageMaker Neo can deploy models to edge devices. Automatic scaling for endpoints is possible. Shadow testing evaluates new model against currently deployed model to catch errors.

Multiple ways exist to work with SageMaker, the most common one is by using its associated notebook. This notebook runs on an EC2 instance and has access to S3 and thus associated training data. It allows use of scikit_learn, tensorflow, Spark and has access to a wide variety of built-in models that can be accessed via pre-built Docker images. From the notebook you can also launch training instances and endpoints.<br>
A lot of this can also be done via the SageMaker console.<br>

Let's look at SageMaker's built in algorithms.<br>
Linear learner performs linear regression. It can also handle binary and multi-class classification. It is not accurate on data as it is limited to straight lines as indicated in image below.<br>
![Screen Shot 2024-06-24 at 13 43 15](https://github.com/artainmo/DevOps/assets/53705599/f5eaeb28-34c7-4942-8cd3-94744ca68a81)<br>
It supports both file and pipe mode. Where file mode will copy all training data in a file to every training instance while pipe mode will pipe and stream it from S3. Pipe mode is faster.<br>
As instance type single or multi-machine CPU or GPU can be used. Having multiple GPU on same machine isn't helpful however.

eXtreme Gradient Boosting (XGBoost) consists of a series of decision trees where new trees are made to correct the errors of previous trees. It is fast and has been winning a lot of Kaggle competitions. As it uses decision trees it is used for classification. However, using regression trees it can also perform regression.<br>
One hyperparameter is *max_depth* which refers to the tree depth. Too much depth can lead to overfitting.<br>
It can be trained on a single-instance GPU such as P2 or P3 for faster training which can also be more cost effective. To use GPU, set *tree_method* hyperparameter to *gpu_hist*. 

SageMakers Seq2Seq algorithm takes as input a sequence of tokens and outputs a sequence of tokens. Machine translation, text summarization, speech to text, are common uses of this. It can be used both on RNNs and CNNs.<br>
Its training data must be tokenized beforehand. Next to training and validation data, you also need to provide vocabulary files. Even on SageMaker, training for machine translation can take days. Else, pre-trained models are available and public training datasets too.<br>
BLUE score and perplexity are well-suited for evaluating machine translation models.

DeepAR uses RNNs and is used to forecast one-dimensional time series data.<br>
It is recommended for training to use CPU and move up to GPU only if necessary for larger models or mini-batch sizes (>512). For inference/predicting only CPU is supported.

BlazingText can be used for text classification such as predicting labels for a sentence. It is useful for information retrieval.<br>
It can also perform word2vec which consists of creating vector representations of words. This is also called word embedding. It is of use in NLP. Different modes exist such as Continuous Bag of Words (CBOW) where word order does not matter, skip-gram which uses n-grams, and batch skip-grams which distributes computation over many CPU nodes.

Object2vec is an embedding layer, thus it transforms into vectors. Those vectors can be compared and thus evaluated for similarity. Object2vec is more general purpose than word2vec in that it works on arbitrary objects. Thus while word2vec only transforms words, object2vec can transform entire documents. Object2vec can for example be used to compute nearest neighbors of objects, but also predict genres of music/movie, or for recommendation systems.<br>
As instance type only one machine can be used with CPU, GPU or multi-GPU.

Object Detection algorithms in SageMaker detect and classify all objects in an image using a deep neural network. The predicted classes are given with a confidence score.<br>
Separate algorithms exist for MXNet and Tensorflow.<br>
Object Detection algorithms can be trained from scratch or pre-trained models can be used.<br>
As instance type for training you can use GPU, multi-GPU, multi-machine while for inference/predicting you can use CPU or GPU.

While Object Detection algorithms tell you where an object in an image lies, Image Classification algorithms assign one or more labels to an image.<br>
Separate algorithms exist for MXNet and Tensorflow.<br>
Weight decay is a hyperparameter that often comes forward in SageMaker's build-in algorithms which refers to L2 regularization.<br>
As instance type for training you can use GPU, multi-GPU, multi-machine while for inference/predicting you can use CPU or GPU.

Semantic Segmentation is pixel level object classification. It produces a segmentation mask that maps individual pixels to labels or classifications. Self-driving cars or medical imaging diagnostics for example need such a level of precision.<br>
It is built on MXNet Gluon and Gluon CV. Three algorithms can be choosen from, Fully-Convolutional Network (FCN), Pyramid Scene Parsing (PSP), DeepLabV3. Architectures such as ResNet50, ResNet101 are trained on ImageNet and define the model's hyperparameters/backbone for you. You can train from scratch or start with ImageNet and build upon that.<br>
It can only be trained on a single machine with GPU. For inference/predicting both CPU and GPU can be used.

Random Cut Forest is Amazon's unsupervised algorithm for anomaly detection. It looks at series of data and tries to find anomalies by giving an anomaly score to each data point.<br>
It works by creating a forest of trees where each tree is a partition of the training data, then after adding a data point to a tree, it looks at how the tree changes. If it changes a lot due to that data point, the data point may be anomalous.<br>
Can use file or pipe mode.<br>

The Neural Topic Model tries to identify what the topic of a document is. It is unsupervised.<br>
Can use file or pipe mode.<br>
The main hyperparameter *Num_topics* defines how many topics you want.<br>
GPU is recommended for training. CPU is cheaper and can be used for inference/predicting.<br>
Latent Dirichlet Allocation (LDA) is another topic modeling algorithm. It is also unsupervised but contrary to the Neural Topic Model it doesn't use deep learning. It can also be used for things other than words that are based on unsupervised clustering such as clustering customers based on purchases or performing harmonic analysis of music. Its training is done on single-instance CPU.

K-Nearest-Neighbors (KNN) is a simple classification or regression algorithm. When using this algorithm SageMaker includes a dimensionality reduction stage and builds an index for looking up neighbors faster.<br>
It can be trained on CPU or GPU instances. For inference/predicting both CPU and GPU can be used. CPU can provide lower latency but GPU provides higher throughput for handling large batches of data all at once.

K-means is an unsupervised clustering technique. It divides data into K groups where members of a group are as similar as possible to each other. Euclidian distance can be used to measure similarity. SageMaker allows large scale K-means clustering.<br>
Both CPU and GPU instance types can be used but CPU is recommended.

Principal Component Analysis (PCA) is a dimensionality reduction algorithm. It is unsupervised. It transforms higher-dimensional data, meaning data with a lot of different features, into lower-dimensional data, such as 2D data to allow plotting, while minimizing the loss of information. The reduced dimensions are called components and they are ordered so that the first one has the largest variability and thus predictive power. It works by creating a covariance matrix that it distills down with the singular value decomposition (SVD) algorithm.
Can use file or pipe mode.<br>
As instance types it can use GPU or CPU.

Factorization Machines specialize in classification or regression with sparse data. Item recommendation is an example of sparse data as a lot of item pages exist but the client only saw some of them, thus we don't have a lot of data on the client's interests. Factorization Machines are a supervised method and are usually used in the context of recommender systems.<br>
CPU and GPU can be used but CPU is recommended because GPU is only useful when data is dense while Factorization Machines are useful when data is sparse.

IP Insights is an unsupervised technique that learns the usage patterns of specific IP addresses to then identify suspicious behavior from those IP addresses such as login attempts from anomalous IP addresses. Thus it is a security tool.<br>
As instance types CPUs and GPUs can be used but GPUs are recommended as it uses a neural-network. Multiple GPUs can be used on one machine.

Reinforcement learning (RL) is different. It learns how to navigate a virtual environment optimally as different states are encountered within that environment.<br>
Let's use the Pac-Man game as an example. RL uses an agent (in this example the agent is Pac-Man) that explores some space (in this example the space is the gameboard) and by doing that learns the values/rewards associated with different state changes and conditions (in this example running in a wall would be negative while in a power pill would be a reward). Thus the agent learns for a given position what is best done within an environment with surroundings.<br>
RL is often used for machines playing games, but it can also be used for supply chain management, industrial robotics, HVAC systems and autonomous vehicles. Once the space has been explored it yields fast online performance.<br>
Q-Learning is a specific implementation of reinforcement learning. 'States' refer to surroundings (for this example if a wall or ghost is next to pac-man). Each state and possible action has a Q value starting at 0 that decreases as negative things happen while exploring the space and increases as rewards happen while exploring the space on a specific state/action. Then we can use those Q values to inform the agent's future choices (in this example Pac-Man's future actions).<br>
SageMaker offers a RL implementation built on deep learning that uses Tensorflow and MXNet. It also supports toolkits such as Intel Coach and Ray Rllib and environments who can be custom, open source or commercial. It can also distribute across cores and instances the exploration/training and environment rollout.<br>
Because it is build on MXNet and Tensorflow for deep learning using a GPU is probably best. It supports multiple instances and cores.

Finding the optimal value for hyperparameters is difficult. Some guidance exists but often one needs to experiment to find the best value. This experimenting can become tedious and costly when having a lot of hyperparameters. SageMaker tries to resolve this problem via Automatic Model Tuning. With this you only need to define the important hyperparameters with value ranges you want to try, and the metrics you want to optimize the model on. Then SageMaker will launch 'Hyperparameter Tuning Jobs' that train as many combinations as you allow. The set of hyperparameters producing the best results can then be deployed as a model. It doesn't need to try every combination as it can learn if a value direction is negatively affecting results. One way of limiting costs yourself is to define smaller hyperparameter value ranges.

Apache Spark is a popular framework for processing data and it also has a powerful MLlib that can perform large scale ML. Spark loads data in DataFrames, then you can distribute the processing of that DataFrame across an entire cluster on Spark.<br>
AWS allows use of sagemaker-spark library where you can pre-process your data with Apache Spark but afterwards use SageMakerEstimator instead of MLlib which exposes some popular SageMaker algorithms you can use in Spark such as K-means, PCA, XGBoost to produce a SageMakerModel to make inferences/predictions.<br>
In practice you can take a SageMaker notebook and connect to a remote EMR running Spark. Then pre-process the training DataFrame, and afterwards call *fit* method on SageMakerEstimator to get a SageMakerModel on which you can call *transform* to make inferences.<br>
This allows combining pre-processing big data in Spark with training and inference/predicting in SageMaker to get best of both worlds.

SageMaker Studio is an integrated development environment (IDE) for machine learning. It allows the creation and sharing of Jupyter notebooks. SageMaker Experiments is present in SageMaker Studio and lets you compare and search your notebooks and ML jobs to find model with best performance.

SageMaker Debugger saves the internal model state at periodical intervals while training. This allows looking back at gradients during training but also system resource usage. You can define rules that will detect unwanted conditions during training and notify in CloudWatch or using SNS. It also integrates with SageMaker Studio as the SageMaker Studio Debugger dashboard to form a visual environment. It can also automatically generate training reports.<br>
It supports Tensorflow, PyTorch, MXNet, XGBoost, SageMaker generic estimator and it also has APIs available in Github.<br>
The SageMaker Debugger Insights Dashboard displays what happens during training using graphs.

SageMaker Autopilot performs AutoML in SageMaker. This automatically searches what the best model/algorithm and associated tuning is to make predictions based on data. It automates algorithm selection, data preprocessing, model tuning and associated infrastructure creation. It finds the optimal solutions via trial and error.<br>
To use it you first need to load data from S3 for training, then select target column for prediction. After finding the best model automatically it will provide a notebook for you to see what it has done and tweak it if you want. Thus Autopilot can be used as a starting point where you still apply own judgment and refinement. A model leaderboard will also be presented to display a ranked list of recommended models. Then you can deploy the model you selected from recommendations, monitor it over time, and even refine it via the notebook.<br>
Autopilot has different training modes. One is HPO where after selecting the most relevant algorithm/model it will select the best ranges of hyperparameters and run 100 tests by default to find optimal hyperparameters. To limit costs Bayesian optimization is used if dataset is smaller than 100MB else multi-fidelity optimization is used to stop poorly performing trials early. Another training mode is ensembling that trains several models at once. It runs 10 trials with different model and parameter settings. The Auto mode will use HPO if dataset is larger than 100MB else Ensembling mode.<br>
SageMaker Autopilot can be used for binary classification, multi-class classification or regression. When using Hyperparameter Optimization mode (HPO) you can choose between Linear Learner, XGBoost, deep learning algorithms. When using Ensembling mode you can additionally choose between neural-networks and tree-based methods such as random forests.<br>
SageMaker Autopilot integrates with SageMaker Clarify for AI explainability. It gives transparency on how models arrive at predictions by explaining how different features contribute to each prediction. It works by using SHAP Baselines who use Shapley values, this works by assigning each feature an importance value for each prediction. This indicates what features lended the most weight to a final prediction.

SageMaker Model Monitor provides automatic alerts on quality deviations on deployed models via CloudWatch. It allows visualization of data drift. Data drift refers to the data used to train the model changing over time. For example salary data may increase over time due to inflation. It can also detect anomalies, outliers, new features.<br>
It integrates with SageMaker Clarify which is meant to detect potential bias by explaining model's behavior. It also integrates with QuickSight and SageMaker Studio.<br>
It can monitor drifts in data quality (meaning statistical properties of the features), model quality (such as accuracy, recall, precision), bias (using Clarify), and feature attribution drift (compares feature ranking of training versus live data).

Deployment Guardrails monitors problems that could happen after model deployment. It controls shifting traffic from old to new models until the new model has proven itself functional. It also supports automatic roll-back to return to older model when a problem arises on new model. Shadow tests compare performance of shadow variant by giving it a small traffic part, SageMaker's console monitors it and decides when to promote the shadow variant. 

SageMaker Canvas is no-code ML for business analysts. You only need to provide dataset (from S3 or Redshift), indicate the column to predict, then it will automatically clean data and find best model. It works for classification and regression. Datasets and models can be shared via SageMaker Studio. Time series forecasting is possible but must be enabled for use via IAM role.

SageMaker Clarify has multiple bias metrics to choose from. Bias refers to models not being objective but being biased in their predictions/decisions which we want to avoid to avoid penalizing certain races for example.<br>
Class Imbalance (CI) is a metric that measures if one facet (feature related to a demographic group) has fewer training values than another. Not having equal data for each demographic group can introduce biases.<br>
Difference in Proportions of Labels (DPL) measures the imbalance of positive outcomes between facet values. This means for example certain demographic groups could be overrepresented with positive outcomes biasing the model to predict a positive outcome for this demographic group.<br>
Kullback-Leibler Divergence (KL) and Jensen-Shannon Divergence (JS) measure how much outcome distributions of facets diverge. This means for example how different are loan application outcomes for different demographic groups. Lp-norm (LP) measures the p-norm difference between distributions of outcomes from facets. Total Variation Distance (TVD) measures the L1-norm difference between distributions of outcomes from facets.<br>
Kolmogorov-Smirnov (KS) measures the maximum divergence between outcomes in distributions from facets. This means for example which college application outcomes manifest the greatest disparity by demographic groups.<br>
Conditional Demographic Disparity (CDD) measures the disparity of outcomes between facets and subgroups. This means for example do some groups have a larger proportion of rejection than their proportion of acceptance.

SageMaker Training Compiler is an optimized compiler. In integrates into AWS Deep Learning Containers (DLCs). It compiles and optimizes training jobs on GPU instances. It knows how to take advantage of GPU capabilities to accelerate training up to 50% depending on if you use it well. It converts models into hardware-optimized instructions. It is proven to work on the Hugging Face transformers library, not on own models but you can still use it on own models even if results are not guaranteed. However, with SageMaker distributed training libraries it is incompatible. 

A feature refers to a property used to train a ML model. For example you might predict someone's political party based on 'features' such as their address, income, age... ML models require fast, secure access to feature data for training. A challenge is to keep this data organized and share those features across different models. Instead of storing those features more than once, it is preferred to share them. Data can come from a lot of different places. SageMaker Feature Store help by organizing that data via its feature store where features are categorized into feature groups. Each group will contain record identifiers, feature names, and even event times associated with that feature.<br>
PutRecord API can be used to feed streaming data into Feature Store and GetRecord API to stream data out of it. The Feature Store itself has an online repository and batch repository which refers to offline S3 store. SageMaker Feature Store will automatically create a Glue Data Catalog for the offline S3, then tools can be used such as Athena or other services that integrate with S3. Alternatively to streaming, data can also be loaded directly into the offline S3 store.<br>
For security it encrypts at rest and in transit, KMS can be used. IAM can be used to manage access control and AWS PrivateLink for secured exposure.

SageMaker ML Lineage Tracking automates lineage tracking. Lineage Tracking is a data management practice that tracks the life cycle of data, including its origin, transformations, and usage over time.<br>
SageMaker ML Lineage Tracking will automatically create and store ML workflows. We call this more broadly MLOps, a field that keeps track of all the pipelines and processes that go into a ML workflow.<br>
It can track various entities, one is a trial component such as for example a processing job, training job or a transformation job. Those trial components can be assembled into a trial representing a model composed of trial components. Grouping trials together we call an experiment. Context refers to a logical grouping of any entities. Actions refer to workflow steps such as model deployment. Artifacts (objects or data such as S3 bucket or a docker image in ECR) are generated along the way. Lastly, associations can be specified between entities using specific tags.<br>
Once you have a lineage you can query it using LineageQuery API which is part of SageMaker's SDK for Python. ML Lineage Tracking can also produce visualizations by using an external visualizer helper class.<br> 
ML Lineage Tracking integrates with AWS Resource Access Manager for cross-account lineage.

SageMaker Data Wrangler is an ETL pipeline baked into SageMaker Studio. Thus it is a visual interface to prepare data for machine learning. It allows importing, visualizing, transformation of data. It has 300+ built-in transformations or you can integrate own transformations using Pandas, PySpark, or PySpark SQL.<br>
Quick Model allows training model with a subset of that data and measure results. This allows experimenting with data processing optimization.<br>
Data Wrangler lies between data sources and places to send it to.<br>
![Screen Shot 2024-06-25 at 18 27 41](https://github.com/artainmo/DevOps/assets/53705599/68de8bbb-88ca-4680-a864-fba3c1a67cc4)<br>
Data Wrangler isn't doing the transformations of your pipeline itself, it's just generating code to do those transformations in your pipeline. Thus it is more a code generation tool. It will export the code to a notebook for execution. 

### High-Level ML Services
Higher level ML services offered by AWS are aimed for a general audience not for ML experts.

Amazon Comprehend is an NLP engine that provides analytics of the documents fed into it. Those documents can come from any number of sources, such as social media, emails, web pages, raw documents, transcripts. A separate product called Comprehend Medical can also take medical records. It can extract key phrases from those documents, but also entities (for example restaurant name, menu item, person name...), and topics to classify documents. It can perform sentiment analysis, detect languages, events, personally identifiable information (such as address, social security number or credit card number). Targeted sentiment anaysis is also possible and refers to sentiment relative to a specific entity. It can also extract syntax which refers to word's part of speech such as nouns, verbs, punctuations.<br>
Comprehend can be extended by training it on own data.

Amazon Translate uses deep learning to translate text. It supports custom terminology where you specify certain words and their translations. Before translating it can detect languages itself.

Amazon Transcribe does speech to text. It can also support streaming audio and automatically identify the dominant language. It can also identify speakers, not actual name but as speaker 1, speaker 2... It can also perform channel identification, meaning for example if you have two callers you could transcribe them separately and then merge those transcriptions. It can also take a custom vocabulary list for words it might not know about. Even custom vocabulary tables who also indicate the unknown words' pronunciation.<br>
Amazon Transcribe Call Analytics is trained specifically for customer service and sales calls. It can take the audio from a call with a customer, this saves people from taking notes. It can also capture the overall sentiment, talking speed, one speaker interrupting the other, specific phrases such as 'cancel my subscription'.<br>
Amazon Transcribe Medical is trained specifically on medical terminology. It takes patient privacy in account by being HIPAA-eligible.<br>
Amazon Transcribe Subtitling provides live subtitles.

Amazon Polly does text to speech in many different voices and languages.<br>
It contains Lexicons which allows customization of pronunciation of specific words and phrases. For example 'W3C' being pronounced as 'World Wide Web Consortium'.<br>
It supports Speech Synthesis Markup Language (SSML) format which is an alternative to plain text. With SSML you can indicate the desired pronunciation (breathing, whispering, speech rate, pitch, pauses) of plain text.<br>
It also supports Speech Marks which encode when a sentence/word starts and ends in the audio stream. This is useful for lip-synching animation.

Amazon Rekognition performs computer vision. Its main purpose it object and scene detection. Own face collection can be used for Rekognition to identify individuals by their name. Else it can perform facial analysis to identify gender, age, emotion, next to celebrity recognition and comparing faces. It can also perform image moderation to flag inappropriate images. It can extract text within an image. Else it can perform video analysis to mark the timeline where an object/individual was detected. People pathing it can do too whih refers to the path someone follows in a scene over time.<br>
Images come from S3 or via the API raw image bites can be sent. Videos must come from Kinesis Video Streams. Lambda can be used to trigger image analysis via Rekognition upon S3 image upload.<br>
Rekognition Custom Labels allows extension of Rekognition's labeling capabilities by providing a small set of labeled images containing labels Rekognition doesn't know yet.

Amazon Forecast is a time series forecasting service using ML. It has 'AutoML' option that chooses best model for time series data. It can be used for inventory planning, financial planning, resource planning.<br>
Different algorithms can be used by Forecast. You don't have to select one yourself as Forecast chooses the best one automatically with 'AutoML'.<br>
Convolutional Neural Network - Quantile Regression (CNN-QR) is computationally expensive and best for large datasets with hundreds of time series. It can also accept related historical time series data and metadata.<br>
DeepAR+ is also computationally expensive and best for large datasets. It uses a RNN and accepts related forward-looking time series data and metadata.<br>
Prophet is an additive model that can handle non-linear trends and seasonality. In an additive model, we represent a particular observation in a time series as the sum of T (trend), S (seasonality), C (cyclical variations), I (irregular variations). Trend refers to the linear increasing or decreasing behavior of the series over time while seasonality refers to the repeating patterns or cycles over time.<br>
Non-Parametric Time Series (NPTS) is well suited for sparse data. Data sparsity refers to the scenario where a large percentage of data within a dataset is missing or is set to zero.<br>
Autoregressive Integrated Moving Average (ARIMA) is a good choice for simple datasets of less than 100 time series.<br>
Exponential Smoothing (ETS) is appropriate for simple datasets of less than 100 time series.

Amazon Lex is the same technology that powers the Alexa device by Amazon. Alexa uses Amazon Transcribe to transform speech to text, Lex to handle the request and Amazon Polly to transform text back to speech.<br>
Lex is a chatbot engine build around intents. An utterance/phrase (ex. 'I want to order a pizza') invokes an intent. A lambda function can fulfill that intent. Slots specify the extra information needed for the intent (ex. Pizza size, toppings, delivery address, are slot values).<br>
Amazon Lex can be deployed to AWS Mobile SDK for mobile apps, Facebook Messenger, Slack, and Twilio.<br>
Amazon Lex Automated Chatbot Designer automates the process of creating a chatbot. It takes transcripts and uses NLP and deep learning to extract intents and slot values. It can take transcripts form Amazon Connect. Amazon Connect can be used to build a call center. It is a cloud-based virtual contact center that can receive calls and listen to those calls with Amazon Lex. 

Amazon Personalize is a fully managed recommendation engine. Amazon uses it on its webshop to propose other products.<br>
It can be used via an API that takes customer data and sends back recommendations. The 'GetRecommendations' API can send recommended or similar products. The 'GetPersonalizedRanking' sends a ranking of products you want to propose.<br>
It allows recommendations for new unknown users by recommending popular items. Contextual recommendations that take in account contextual factors such as device type, time of day, location, are also possible. It can also be used to segment users intelligently into different groups for marketing campaigns.<br>
Filters can be used for example to avoid recommending already bought products and business rules for example to highlight premium content. It can also inject promoted content into recommendations and find the most relevant promotion.<br>
'Recipes' is a terminology in Amazon Personalize that refers to the different model types. One type is USER_PERSONALIZATION meaning you want recommendations for a specific user. PERSONALYZED_RANKING returns a given list in a ranked manner for a specific user. Lastly, RELATED_ITEMS provides similar items for a given item. Another terminology is 'solutions' which represents the model and is responsible for training the model. It can optimize not only for relevance but also custom objectives. It can also perform HPO. 'Campaigns' is another terminology that means deploying your 'solution' version with enough capacity for real-time recommendations.<br>
To maintain relevance of recommendations keep your dataset current, meaning you keep feeding it the latest data. Also you can do a full retrain of the model once a week and incremental retraining every two hours.<br>
For security, data is not shared across accounts, KMS can be used for encryption, IAM is used for access control to the service, inappropriate bucket policies in S3 could hinder Personalize from processing its data, monitoring occurs via CloudWatch and CloudTrail.<br>
For data ingestion you pay per GB. For training per hour. For inference/predicting you pay per TPS-hour (average transactions per seconds over each hour). When using batch instead of real-time recommendations you pay per user or item.

Amazon Textract performs optical character recognition (OCR). An image of text it can turn into text data. It can also handle forms, fields, tables, and structure data automatically.<br>
AWS DeepRacer is a reinforcement learning powered 1/18-scale race car. It is more of an education tool used to play in race car competitions where the best model wins.<br>
Amazon Lookout comes in three flavors, one for equipment, another for metrics, and lastly vision. It is an industrial application that takes data and detects abnormalities. It will for example detect abnormalities from sensor data to automatically detect equipment issues. When monitoring metrics the associated data can come from S3, RDS, RedShift, other third party apps. Lookout for vision uses computer vision to detect defects and is primarily used for electronics manufacturing.<br>
Amazon Monitron is an end-to-end system for monitoring industrial equipment and perform predictive maintenance too. Predictive maintenance refers to warning about equipment potentially failing in the future after detecting data abnormalities. Compared to lookout it is self-contained and higher-level. Monitron sensors can be used to capture vibration, temperature, or other metrics and warn about abnormalities via the Monitron app.

TorchServe is part of the PyTorch project and is a collaboration between Amazon and Meta. It is a model serving framework for PyTorch. It deploys PyTorch models which integrates with AWS for hosting.<br>
Amazon developed its own microship for deep learning and calls it AWS Inferentia chip. EC2 Inf1 instance type uses this chip. AWS Neuron is an SDK for optimizing models running on the Inferentia chip. It is automatically integrated with SageMaker and deep learning AMIs, deep learning containers, and it can integrate with Tensorflow, PyTorch, MXNet.<br>
AWS Panorama brings computer vision at the edge. It deploys computer vision models close to your cameras. Some cameras can even have AWS Panorama built in, or other cameras can use the AWS Panorama appliance to connect to Panorama. The results can be routed to S3 or CloudWatch.

AWS DeepComposer is an AI powered music keyboard for educational purposes performing machine-generated music. You provide a melody and it produces a song from that.<br>
With Amazon Fraud Detector you can upload own historical fraud data. It will automatically build a custom model from the template you choose. It exposes an API for your online applications. It assesses risk from new accounts, 'try before you buy' abuse, online payments.<br>
Amazon CodeGuru is ML-powered code reviews. It can be fed source code from GitHUb, BitBucket, or AWS CodeCommit, and it will automatically analyze that code to find imperfections that hurt performance, resource leaks, race conditions. It will also fix security vulnerabilities. It supports Python and Java.<br>
Contact Lens is built for Amazon Connect's customer support call centers. It ingests audio data from recorded calls and transcribe which allows the search of specific calls back. It can also perform sentiment analysis and find correlations between customer utterances/phrases and successful calls. It categorizes calls automatically. It measures talk speed and interruptions which can for example give feedback to customer service on how to talk better. It can also detect themes to discover emerging issues for example.

Amazon Kendra is aimed at enterprise search with natural language. It can provide internal tech support by answering for example: 'Where is the IT support desk?' or 'How do I connect to my VPN?'. It can combine data from internal file systems into one searchable repository. It is ML-powered and uses thumbs up/down feedback to improve over time.<br>
Amazon Augmented AI (A2I) is a tool for performing human reviews of machine learning predictions. It is similar to SageMaker GroundTruth but the difference is that it automatically builds workflows for reviewing low-confidence predictions. Amazon Mechanical Turk is where the human workforce comes from. It integrates with SageMaker, Amazon Textract and Rekognition.

### ML Implementation and Operations
ML models in SageMaker are hosted in Docker containers. Inside this container we can find a pre-built deep learning model, a pre-built scikit-learn or Spark ML model. A container can contain Tensorflow, MXNet, Chainer or PyTorch code. Tensorflow is not distributed across machines automatically. The framework Horovod, or Parameter Servers can be used to distribute Tensorflow training across multiple machines. A pre-built docker image can be used and even extended by own code.<br>
Docker containers are created from docker images and images from Dockerfiles. An image gets stored in a repository, for SageMaker this would be Amazon Elastic Container Registry (ECR).<br>
The structure of a training container is shown in following image.<br>
![Screen Shot 2024-06-27 at 16 27 14](https://github.com/artainmo/DevOps/assets/53705599/cca0c445-7ae1-4e73-89b8-5f6861c3a03a)<br>
The model directory is used for deployment. Here is the structure of a deployment container.<br>
![Screen Shot 2024-06-27 at 16 29 29](https://github.com/artainmo/DevOps/assets/53705599/5431499c-0894-4ef3-a1e6-2d63da6fadbb)<br>
The structure of a docker image that combines training and inference looks like the following image. The possibility also exists to use separate images for training and inference.<br>
![Screen Shot 2024-06-27 at 16 30 45](https://github.com/artainmo/DevOps/assets/53705599/a1eab729-50d0-488f-9cee-88d8d77067b8)<br>
'nginx.conf' is a configuration file for the NGINX web server. 'predictor.py' implements a flask web server for making predictions at runtime. The 'serve' directory contains a program for container hosting. The 'train' directory contains the invoked program for training. 'wsgi.py' is a wrapper for invoking flask application to serve results.<br>
Production variance allows testing out multiple models on live traffic. Variant weight indicates how to distribute traffic among them. A new model iteration could start with 10% variant weight and when proven performant the variant weight could be increased.

Examples of edge devices are an embedded computer within your self-driving car, a smart camera like AWS deep lens. SageMaker Neo compiles inference/predicting code to edge devices. It optimizes code for specific edge devices such as ARM, Intel, Nvidia processors. Having the inference model run locally on edge device allows for speed by eliminating web request latency. Neo accepts code writtin in Tensorflow, MXNet, PyTorch, ONNX, or XGBoost.<br>
Neo pairs well with AWS IoT Greengrass as Greengrass deploys code on an Edge device. Thus the model is trained in cloud with SageMaker, compiled with Neo, and deployed on edge devices with IoT Greengrass.

For security, use IAM to restrict permissions for users and services, use multi-factor authentication whenever possible. Use SSL/TLS when connecting to anything. Use CloudTrail to collect forensic information when necessary. Use encryption, especially with PII both in rest and at transit.<br>
At rest, in SageMaker jobs and notebooks, KMS can be used for encryption. In docker containers everything under '/opt/ml' and '/tmp' can also be encrypted with KMS. S3 buckets containing training data can also be encrypted with KMS. S3 can also be used to host trained models and again KMS can encrypt this.<br>
In transit, all traffic supports TLS and SSL. IAM roles can be used to limit SageMaker's access to resources. Even inter-node training communication can be encrypted. However, this would increase training time and cost.

SageMaker's training jobs run in a VPC. For extra security a private VPC can be used. SageMaker depends on S3 for training data and model artifacts. Within a private VPC you will need VPC endpoints to enable communication with S3.<br>
SageMaker notebooks are internet-enabled by default which can be a security hole. This can be disabled, but then to access S3, you will need an interface endpoint, also called PrivateLink, or instead a NAT Gateway.<br>
Training and inference containers are also internet-enabled by default. Network isolation is possible but again it would prevent S3 access.<br>
When using IAM on SageMaker you can set the following user permissions: CreateTrainingJob, CreateModel, CreateEndpointConfig, CreateTransformJob, CreateHyperParameterTuningJob, CreateNotebookInstance, UpdateNotebookInstance. IAM predefined policies we can use are: AmazonSageMakerReadOnly, AmazonSageMakerFullAccess, AdministratorAccess, DataScientist.<br>
Cloudwatch can log, monitor and alarm on endpoint invocations and latency. It can also monitor the node health, CPU and available memory. It can even monitor Ground Truth to see how active human workers are. CloudTrail records actions from users, roles and services within SageMaker. Its log files are delivered to S3 for auditing.

A general rule for choosing an instance type is that deep-learning benefits from GPU instances (P3, g4dn) for training. But inference/predicting is less demanding and thus a lightweight compute instance (C5) can be sufficient. For training non-deep-learning algorithms a general purpose compute instance (M5) can be a good fit. Even if GPU costs more, in the end it can be more cost effective than CPU due to its better performance on certain models.<br>
Using EC2 Spot instances can save costs up to 90% over on-demand instances. The catch with Spot instances is that they can be interrupted at any time. Checkpoints can be used to S3 for training to pick up where it left off. Waiting for a Spot instance to become available can increase training time.

Elastic inference accelerates deep learning algorithms at the inference stage. And it does this at a fraction of the cost of using a dedicated GPU instance. It works by adding an elastic inference accelerator machine type alongside the CPU instance on which the inference model runs. The cost of the CPU together with elastic inference (EI) accelerator machine is going to be less than using a GPU instance, while still performing well.<br>
Notebooks can also use EI accelerators which will work with Tensorflow and MXNet pre-built containers. Custom containers should use EI enabled Tensorflow or MXNet. EI accelerator can also be used on SageMaker's built-in Image Classification and Object Detection algorithms.<br>
*Be aware that as of April 2023, AWS is no longer allowing new users to use Elastic Inference. They are phasing it out in favor of 'more cost effective' solutions. We're not sure if the exam reflects this reality yet, but expect any mentions of Elastic Inference to go away over time.*
SageMaker allows Automatic Scaling to add or remove inference nodes as needed. You can create scaling policies to define target metrics, min/max capacity, cooldown periods. It works with CloudWatch which monitors the performance of inference nodes to know when scaling is needed. It is recommended to load test your configuration before using it to make sure created policies work as expected.<br>
SageMaker will automatically attempt to distribute your instances across different availability zones for better resiliency, but for such a distribution to be possible you need more than one instance. VPC should be configured with at least two subnets, so each of them can be in different availability zone.

To use Serverless Inference, specify your container, its memory and concurrency (multiple computations simultaneously) requirements, it will then select the necessary amount of hardware. Thus the underlying capacity for your inference is automatically provisioned and scaled. When no requests are coming in it can even scale down to zero. This is useful when traffic is infrequent or unpredictable. You pay based on usage thus this on-demand pricing can be economical. Via CloudWatch we can monitor ModelSetupTime, Invocations, and MemoryUtilization.<br>
Amazon SageMaker Inference Recommender recommends what instance types to use and what configuration to use for your models. It automates load testing, model tuning and deployment to an optimal inference endpoint type. It can run in different modes. One is 'instance recommendations' where it runs load tests on recommended instance types for 45min, thus it provides a quick answer. 'endpoint recommendations' performs custom load tests on the instance types, traffic patterns, latency and throughput requirements you specify, which takes +-2hours.

Inference Pipelines allows chaining multiple inference containers into one pipeline of results. It can create linear sequences of 2-15 containers. For example you can combine your pre-processing, predictions and related post-processing, all in different containers who are chained together. It can handle both real-time inference and batch transforms.

MLOps refers to managing the pipeline/workflow surrounding the building, testing and deployment of ML models.<br>
A Kubernetes pipeline based ML infrastructure can be integrated in SageMaker using Amazon SageMaker Operators for Kubernetes or Components for Kubeflow Pipelines. Hybrid ML workflows where Kubernetes lies partly on-premises and is partly integrated with SageMaker in cloud is possible. This may be desirable if some sensitive information should stay on premises. SageMaker Operators can be installed on Amazon Elastic Kubernetes (EKS) to create SageMaker jobs via the Kubernetes API. Components for Kubeflow Pipelines integrates SageMaker with the Kubeflow MLOps solution under Kubernetes. Different components are available to use within the Kubeflow pipeline such as for processing, hyperparameter optimization, training and inference in SageMaker.<br>
It is possible to have MLOps in SageMaker only, without using Kubernetes, via SageMaker Projects. SageMaker Projects is SageMaker Studio's MLOps solution with CI/CD. Such a pipeline allows building images, process data, train, evaluate, deploy and monitor/update models. For building and deploying ML solutions it will use code repositories and for defining/chaining the steps it will use SageMaker Pipelines.  

### Generative AI: Transformers, GPT, Self-Attention, and Foundation Models
RNNs introduced a feedforward loop to propagate information forward. This is useful for modeling sequences such as time series or words forming phrases.<br>
Machine translation uses an encoder/decoder architecture. The encoder takes text and passes sequentially, one word at a time, through an RNN. Between each step/word in the RNN a 'hidden state', which contains past information, is passed to the next step/word to not forget prior words' meaning in phrase. In the end we have a last hidden state as output of the RNN which encodes the meaning of the phrase. The decoder will take that hidden state and turn it back into tokens/words.<br>
The problem with this hidden state, represented as a vector, encoding the whole phrase/text, is that the information it can contain is limited which results in the information related to the start of the sentence being diluted for long phrases. Thus RNNs don't perform well on long phrases/sequences and are not the best approach for machine translation.<br>
In 2017 the academic paper 'Attention is all you need.' resolved this problem by not building one hidden state sequentially but instead produce one hidden state for each word. However, it still cannot be parallelized as those hidden states are computed sequentially.<br>
Transformers use feedforward neural-networks instead of RNNs and a mechanism of self-attention to allow parallelization. Parallelization allows for speed, thus training on much more data, and the creation of large language models (LLMs).

Each encoder or decoder has a list of embeddings (vectors) for each token. Instead of dealing with words, we tokenize those words into numerical representations which we feed into an embedding layer that converts the tokens into a multidimensional vector encoding the words' meaning. Thus similar words have similar embedding vectors.<br>
The job of self-attention is to produce a weighted average of all the token embeddings by computing the attention weights which ties tokens to other tokens who are important for its context and thus meaning.<br>
In the self-attention layer there are three matrices of weights who are learned through backpropagation. Those are the Query, Key and Value matrices. Our embedding matrix gets multiplied by those learned matrices to produce vectors associated with query, key, and value for every token. Then we have to compute a score for each token by multiplying (dot product) its query with each key of every token around it. We call this 'scaled dot-product attention'. To normalize the scores in the end we use softmax.<br>
When reading a phrase we don't know what words come next the word we read. Masked self-attention can be applied to mimick this by preventing tokens from 'peeking' into future tokens. A mask multiplies certain values by zero to cancel them out. GPT uses masked self-attention and is built entirely on decoders while BERT does not and is built on stacks of encoders.<br>
Now we multiply all the values by the scores and add them up which creates a new product vector called Z which represents our updated embeddings for each token. Those will be used inside the feedforward neural-network.<br>
![Screen Shot 2024-06-28 at 14 11 39](https://github.com/artainmo/DevOps/assets/53705599/b4efb1be-7616-4823-ae21-c424ecd48777)<br>
An optimization is multi-headed self-attention. Here, the q, k, and v vectors are reshaped into matrices, then each row of the matrix can be processed in parallel. The number of rows is referred to as the number of 'heads'.

Transformers are the first step into creating chatbots but are not sufficient on their own. Transformers can be used for question answering. By adding the associated layer to transformers we can perform classification such as sentiment analysis. Transformers can also be used for named entity recognition, summarization, code generation, text generation, and translation. 

Generative Pre-Trained Transformers (GPT) is a transformer with a specific architecture. GPT is produced by OpenAI which is a competitor of AWS thus they won't cooperate. While GPT-3 is not open source, GPT-2 and previous models are, thus those can be imported into AWS. We will review GPT-2 as this is the latest model with released details. GPT only consists of decoder blocks. BERT only of encoders while T5 uses both encoders and decoders.<br>
GPT generates the next token over and over, starting with a given sequence of tokens and ending when an end-token is generated. The attention mechanism maintains the relationships between words/tokens to give each word its context. To learn it just needs to receive text as it can try to predict the next word in that text and verify if correct. It uses hundreds of billions of parameters. Hundreds of decoder blocks can be stacked together and they might take thousands of vectors. Each decoder block consists of a masked self-attention layer that feeds into a feedforward neural network. GPT4 is rumored to have well over one trillion parameters.<br>
![Screen Shot 2024-06-28 at 16 23 11](https://github.com/artainmo/DevOps/assets/53705599/3c744485-e262-48e9-ba0a-368142a5b456)<br>
We start with our input words, those need to be tokenized into numerical representations, who are translated into embedding vectors to capture the semantic relationships between tokens, their similarities. Subsequently positional encoding is performed to know where each token is relative to another one. Only then we continue through the decoder blocks. Out of the final decoder block comes an output vector that embeds the meaning of the predicted next token/word. We multiply (dot product) this with our token embedding matrix and the result is a vector that provides the probabilities (logits) of each token being the predicted next token in the sequence. One possibility is to take the highest probability token, which is what GPT would do if temperature setting is set to zero. However by adding temperature we increase the randomness of token selection which allows different responses when running same question multiple times.

Transfer learning with transformers is also called fine tuning. It consists of using a pre-trained GPT or any other transformer model as a starting point, a base representation of how language works. Next we can further train that base model with a specific set of training data to fine tune it for a specific task.<br>
This can be done by feeding the new data through the whole model again.<br>
Or instead you can freeze specific layers and retrain just the top few layers. Freezing layers means you make the parameters (weights and biases) of those layers non-trainable. These parameters will not be updated during the new training process. This preserves the previous learnings, reduces computational load, and prevents overfitting. The top layers of a transformer are more task-specific and can be fine-tuned to adapt the model to the specifics of the new task. By updating the parameters of these layers, you allow the model to learn new patterns and features relevant to the new task.<br>
Lastly, you can add a new layer on top of the trained model to even adapt it to entire new tasks such as classification.

AWS offers foundation models. These are giant pre-trained transformer models we can fine tune for specific tasks.<br>
GPT-3 and above, next to DALL-E (image generation) are owned by OpenAI and are not open source. BERT is owned by Google and not open source. Those won't be on AWS. However, Llama, created by Meta, is open source and found on AWS. Meta's Segment Anything (image generation) is also found on AWS. AWS has aggregated foundation models to offer a suite of foundation models who are sourced from others and themselves. Jurassic-2 created by AI21labs is a multilingual LLM for text generation offered by AWS. AWS also offers Claude by Anthropic which is a LLM for conversations, question answering and workflow automation. They also offer Stable Diffusion from stability.ai for image, art, logo, design generation. Amazon's LLM is called Amazon Titan which can summarize and generate text but also answer questions and provide embeddings.<br>
SageMaker Jumpstart allows launching a new notebook that comes with examples. As option it has 'foundation models' where you can select a foundation model and it will pre-populate a notebook with examples on how to use that foundation model. They integrated a lot of the Hugging Face models. It also provides access to Stable Diffusion for image generation and Amazon Alexa as an encoder/decoder multilingual LLM.

Amazon Bedrock is an API for using foundation models. It is serverless. It also has a fine tuning API to provide labeled examples via S3 to perform transfer learning on those foundation models. It integrates with SageMaker. 

## Resources
[Udemy course - Ultimate AWS Certified Cloud Practitioner CLF-C02](https://campus19.udemy.com/course/aws-certified-cloud-practitioner-new)<br>
[Udemy course - 6 Practice Exams | AWS Certified Cloud Practitioner CLF-C02](https://campus19.udemy.com/course/practice-exams-aws-certified-cloud-practitioner/)<br>
[Udemy course - AWS certified machine learning specialty 2024 - Hands on!](https://campus19.udemy.com/course/aws-machine-learning)<br>
