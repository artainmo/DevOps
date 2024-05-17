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
When creating an EBS we have the 'Delete on Termination' option that is activated by default for the root volume but not other volumes. Thus if you want to preserve the root volume after instance termination you need to deactivate this option.<br>
It is possible to make EBS backups, also called snapshots. Those snapshots can also be copied to other AZs or regions to leverage the global infrastructure.

Amazon machine image (AMI) represents a customization of an EC2 instance. Thus it contains pre-packaged customized software to boot the EC2 instance faster. They can be build for a specific region and be copied to other regions to leverage the global infrastructure.<br>
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

Load balancing allows elasticity by being a server that forwards internet traffic equally to multiple servers (EC2 instances) downstream. Thus it balances the traffic/load across multiple running instances of an application. It does health-checks an if one instance fails it can forward to other instances in other AZs making the application highly-available.<br>
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
The Infrequent Access storage class is for data that is less frequently accessed but when needed requires rapid access. It is cheaper than Standard storage class.<br>
The Glacier storage class is low cost and meant for archiving/backup. You pay for storage and object retrieval. It has the 'Instant Retrieval' option and 'Flexible Retrieval' option with different retrieval time options of 5min to 12hours.<br>
The last storage class is Intelligent-Tiering which allows you to automatically move between storage classes based on usage.

Server-side encryption means that the uploaded file/object on S3 will get encrypted automatically by the server. Client-side encryption is when the user encrypts the file/object before uploading it. Both exist on AWS but by default server-side encryption is always on.

IAM Access Analyzer is a monitoring feature to ensure that only intended people have access to S3 buckets. It works by analyzing the various related policies. It will indicate what buckets are publicly available or shared with whom.

The shared responsibility model of AWS states that amazon is responsible for the infrastructure while the client is responsible for S3 versioning, bucket policies, replication setup and data encryption.

AWS Snow Family represents a highly-secure, portable/offline device to collect and process data at the edge, and migrate data into and out of AWS.<br>
The edge refers to a location where internet is limited to non-existent, this makes online data uploads and processing too slow to impossible. Examples are a truck on the road, ship on the sea, an underground mining station. This is why Snow Family devices are used to process data, and store data to upload in the actual S3 cloud later by shipping the device to it.<br>
Edge computing is processing data while it is being created in an edge location.
For data migration we have the following devices in ascending order of storage capacity, the Snowcone (8TB storage), Snowcone SSD (14TB), Snowball Edge (petabytes of storage) and Snowmobile (exabytes of storage). While for edge computing, only the Snowcone and Snowball Edge can be used.<br>
AWS OpsHub is a software with a UI to use your AWS Snow Family device.<br>
For Snowball Edge you pay for device usage and data transfer out of AWS.

AWS Storage Gateway is used to bridge on-premise data and cloud data in S3 when using a Hybrid Cloud. It allows on-premise to seamlessly use the AWS Cloud. It can be used for creating and restoring backups.

### Databases & Analytics
Storing data on disk as with EFS, EBS, EC2, Instance Store and S3 can have its limits. This is why you sometimes want to store data on a database where you can structure the data, build indexes for efficient database searches, and define relationships between datasets.<br>
Relational databases enable linking datasets and the use of SQL queries.<br>
NoSQL databases are non-relational and don't use SQL. It is flexible and scalable. Different types exist for optimization of specific data models.

Amazon Relational Database Servive (RDS) is a managed service for the use of a SQL database in the cloud. We can also deploy own databases on EC2. But the advantage of RDS is that it is managed by Amazon.<br>
Amazon Aurora is a database technology who supports PostGreSQL and MySQL, because it is cloud optimized, performances on PostGreSQL and MySQL is more efficient. It is more expensive than RDS but more efficient. Aurora serverless has no management overhead and is useful for infrequent workloads.

RDS Read Replicas can scale the read workload of your database.<br>
Multi-AZ gives high availability by providing a replication of the database into another AZ.<br>
Multi-Region creates Read Replicas across regions which is useful for disaster recovery and local performance for global reads.

Amazon ElastiCache is used for managed Redis or Memcached databases. Those databases are cache-based which we call in-memory database. Caches have low latency but smaller storage capacity. Thus ElastiCache is fast but of smaller capacity like a RAM in a computer.

DynamoDB is a managed, NoSQL, highly-available database with replication across 3 AZs. It is a serverless database because AWS doesn't need to provision any servers. It can scale automatically and has low retrieval latency. It is a key-value database.<br>
DynamoDB Accelerator (DAX) is a managed cache for DynamoDB. Thus as it uses cache it is 10X faster.<br>
DynamoDB Global Tables make a DynamoDB table accessible with low latency in multiple regions.

Redshift is a database type based on PostgreSQL that is in a warehouse. It is not used for online transaction processing (OLTP), which is what RDS is good for. Instead Redshift is used for online analytical processing (OLAP).

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
This architecture can be reproduced automatically using AWS Elastic Beanstalk. Which is a developer centric view of deploying an application on AWS. It is a PaaS because the client only needs to provide the code. It is limited to certain programming languages or Docker. Within Beanstalk a health agent is present on each EC2 instance and pushes metrics to CloudWatch.<br>
CloudFormation and Elastic Beanstalk are free of use, but you do pay for the resources created.

AWS CodeDeploy automatically deploys or upgrades applications. It works both for EC2 instances and on-premises servers, thus it is a hybrid service.

Before pushing application code to servers you need to store it somewhere. Usually in a git repository like Github. AWS has a competing product called CodeCommit.

AWS CodeBuild allows to build code in the cloud. It compiles source code, run tests, and produce packages who are ready for deployment. In practice, CodeBuild will retrieve the code from CodeCommit, run defined scripts, build the code, to produce a ready to deploy artifact.<br>
CodeBuild is managed, serverless, scalable and secure. You pay as you go.

CodePipeline can be used to connect CodeCommit, CodeBuild and CodeDeploy. CodePipeline automates the steps necessary to push code to production. Those steps are to get the code, build it, test it, provision servers for it and deploy on those servers. It is basically used for CI/CD.

Software packages have dependencies, meaning they depend on each other to be build. Artifact management refers to storing and retrieving those dependencies. AWS CodeArtifact is an artifact manager for software development. Developers and CodeBuild can then retrieve dependencies straight from CodeArtifact.

AWS CodeStar is a unified UI to easily manage software development activities in one place. This is useful when needing to work with the different services used for CI/CD such as CodeCommit, CodeBuild, CodeDeploy, CodePipeline.<br>
It can also be used to edit the code directly in the cloud using AWS Cloud9. AWS Cloud9 is a cloud integrated development environment (IDE), for writing, running and debugging code.

AWS Systems Manager (SSM) helps you manage both EC2 and on-premise systems at scale, thus it is a Hybrid service. It gives operational insight about the state of the infrastructure, it automates patches, it runs commands across all servers and stores parameter configuration with the SSM Parameter Store.<br>
To use SSM we need to install the SSM agent onto our EC2 instances or on-premise system.<br>
SSM has a feature we call SSM Session Manager. It starts a secure shell on EC2 or on-premise servers without the need for SSH.<br>
SSM Parameter Store allows secure storage of configurations and secrets on AWS such as API keys, passwords.

### Leveraging the AWS Global Infrastructure
A global application is an application deployed onto multiple AWS regions or edge locations. The advantage is decreased latency via local deployments being present. Another advantage is Disaster Recovery because if one region goes down, others are still available, this increases the availability of the application. A distributed global infrastructure is also harder to attack.<br>

Route 53 is an AWS service that routes users to the closest deployment with least latency. It is a managed Domain Name System (DNS). DNS associates servers' IPs and URLs.<br>
A web browser first makes a DNS request with an URL to Route 53. Route 53 will return the associated IP address. The web browser will then make its request to the IP address which will return an HTTP response.<br>
Route 53 has different routing policies. The 'Simple Routing Policy' has no health checks and simply returns an IP when a URL gets sent to it. The 'Weighted Routing Policy' distributes traffic across multiple EC2 instances which is similar to load balancing and thus health checks are used. The 'Latency Routing Policy' makes users connect to the closest servers to minimize latency. The 'Failover Routing Policy' performs health checks on primary server and redirects traffic to the failover server if the primary server failed its health checks with the goal of handling disaster recovering.<br>
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
Amazon CloudWatch Logs collects those log files from various AWS services/applications. CloudWatch log agents can be used on EC2 instances or on-premise servers for them to create collectable log files.

Amazon EventBridge (formerly known as CloudWatch Events) allows reactions to events happening in AWS account. Using Cron Jobs you can react to events every x amount of time. Else we can create rules to react to a service doing something.<br>
Events happening from within AWS services are called 'Default Event Bus'. It is also possible to get events from AWS partners which we call 'Partner Event Bus'. Lastly, own custom applications can also send events which we call 'Custom Event Bus'.

AWS CloudTrail is a service enabled by default that provides governance, compliance and audit for own AWS account. It gets the history of events/API-calls made within AWS account by the console, SDK, CLI, AWS services. Those logs can be sent to CloudWatch Logs or S3.<br>
CloudTrail Insights provides automated analysis of CloudTrail Events.<br>
If a resource gets deleted in AWS, CloudTrail should be consulted first as it records the history of events/API-calls made which will help determine who or what deleted the resource.

Debugging on distributed systems is hard because log formats differ across applications and log analysis is hard. AWS X-Ray resolves this problem by providing a visual analysis of own applications after tracing requests made through the distributed applications.

Amazon CodeGuru is a machine-learning-powered service for automated code reviews (CodeGuru Reviewer) and application performance recommendations (CodeGuru Profiler).

AWS Health Dashboard consists of two parts, a Service History and your Account.<br>
The Service History shows all regions' and services' health.<br>
Your Account provides alerts and remediation guidance when AWS is experiencing events that may impact own infrastructure. It provides a personalized view of the performance and availability of the AWS services personally used.

### Virtual Private Cloud (VPC) & Networking 
EC2 instances get a new public IP address every time you stop and restart them. However, private IP addresses are fixed for EC2 instances even if you start/stop them. AWS also has an Elastic IP which can attach a fixed public IPv4 to an EC2 instance.<br>
For public IPs both IPv4 and IPv6 can be used. While IPv4 only allows for private IPs. However, IPv4 costs $0.005 per hour while IPv6 is free.

A VPC is a private network to deploy own resources, for example EC2 instances. One VPC is linked to one region, thus when using multiple regions you will also need multiple VPCs.<br>
Within a VPC we can find Subnets which partitions own network inside own VPC. One Subnet is associated with one AZ and can launch EC2 instances. A public Subnet is accessible from the internet while a private Subnet is not. Route Tables are used to define access to the internet and between Subnets.<br>
A VPC contains a CIDR Range which indicates the range of allowed IP addresses within the VPC.<br>

## Resources
[Udemy course - AWS certified cloud practitioner](https://campus19.udemy.com/course/aws-certified-cloud-practitioner-new)<br>
