**Lesson Objective**
- Describe how compute resources are provisioned and managed in the cloud.
- Compare the benefits and challenges of using virtual servers to managing physical servers on premises.
- Identify the concept of multi-tenancy in Amazon EC2.
# What is Amazon EC2
A more flexible, cost-effective and faster than managing on-premises servers. It offers on-demand compute capacity that can be quickly launched, scaled and terminated with costs based only on active usage.

The flexibility of Amazon EC2 allows for faster development and deployment of applications. Can launch many or few virtual servers as needed and configure security, networking and storage. Can also scale resource up or down based on usage such as handling high traffic or compute-heavy tasks.

**Challenges of on-premises resources**
Imagine that you're responsible for designing company's infrastructure to support new websites. With traditional on-premises resources, must purchase hardware upfront, wait for delivery and handle installation and configuration. This process is time-consuming, costly and inflexible because lock into specific capacity that might not align with changing demands.
![[Pasted image 20260507103653.png]]

**Benefits of using Cloud Resources**
Can quickly launch, scale and stop instances based on needed without the delays and upfront costs associated with traditional on-premises resources.
![[Pasted image 20260507104001.png]]

## How Amazon EC2 works
![[Pasted image 20260507104054.png]]**Launch**
Start by selecting an Amazon Machine Image, which defines the operating system and might include additional software. Also choose an instance type, which determines the underlying hardware resources such as CPU, memory and network performance.

**Connect**
Users or administrators can connect using SSH for Linux instance or Remote Desktop Protocol (RDP) for Window instances. AWS services like AWS systems Manager offer a secure and simplified method for accessing instances. 

**Use**
After you are connected to the instance, can begin using it to run commands, install software, add storage, organize files and perform other tasks.

# Amazon EC2 Instance Types
![[Pasted image 20260507105350.png]]

1. Provides a balanced mix of compute, memory and networking resources. They are ideal for diverse workloads like web services, code repositories and workload performance is uncertain.
2. Instances are ideal for compute-intensive-tasks, such as gaming server, high performance computing (HPC), machine learning and scientific modelling.
3. Used for memory-intensive tasks like processing large datasets, data analytics and databases. They provide fast performance for memory- heavy workloads.
4. Use hardware accelerators like graphics processing units (GPUs), to efficiently handle tasks, such as floating point calculations, graphics processing and machine learning.
5. Designed for workloads that require high performance for locally stored data, such as large databases, data warehousing and I/O intensive application.

## How to Provision AWS Resource
![[Pasted image 20260507112704.png]]

**AWS Management Console**
Web interface for managing AWS services, offering quick access to services, search functionality and simplified workflows. 

With mobile app, you monitor resources, view alarms and check billing, supporting multiple logged-in identities at once.

Good for:  Who prefer visual, easy-to-use interface for managing and configurating AWS services.

**AWS CLI**
Manage multiple AWS services directly from the command line across Windows, macOS and Linux.

Good for: Advanced users and developers who need to automate tasks, script actions and manage AWS resources efficiently from the command line.

**AWS SDK**
Simplifies integrating AWS services into applications by providing APIs for various programming languages. AWS offers documentation and sample code for languages like C++, Java and .NET to help get started.

Good for: Developers looking to integrate AWS services into their application using language-specific APIs

# Launching an Amazon EC2 Instance
https://ap-southeast-1.console.aws.amazon.com/ec2/home?region=ap-southeast-1#Instances:

**Amazon Machine Images (AMI)**
AMI includes the operating system, storage setup, architecture type, permissions for launching, and any extra software that is already installed. Can use 1 AMI to launch several EC2 instances that all have the same setup.

```bash
#!/bin/bash

yum install -y nginx
systemctl start nginx
systemctl enable nginx
```

![[Pasted image 20260507115712.png]]
**3 ways to use AMIs**
- Can create own by building a custom AMI with specific configurations and software tailored to needs
- Can use preconfigured AWS AMIs, which are set up for common operating systems and software.
- Can purchase AMIs from the AWS Marketplace, 3rd party vendors offer specialized software designed for specific use cases.
![[Pasted image 20260507120059.png]]

**AMI repeatability**
- Provide repeatability though a consistent environment for every new instance. Because configurations are identical and deployments automated, development and testing environments are consistent. This helps when scaling, reduces errors and streamlines managing large-scale environments.
![[Pasted image 20260507120336.png]]
# AWS EC2 Pricing
**On-Demand Instances**
Pay any for the compute capacity consume with no upfront payments or long-term commitments required.

- Good for: Critical workloads with strict capacity requirements
  With Amazon EC2 Capacity Reservations, reserve compute capacity in a specific Availability Zone for critical workloads.
  Reservation are charged at the On-Demand rate, whether used or not. Only pay for the instances you run.

**Reserved Instances**
Get a savings of up to 75% by committing to a 1-yea or 3-year term for predictable workloads using specific instance families and AWS Regions.

- Good for: Steady-state workloads with predictable usage
  Offer up to 75% saving over On-demand pricing by applying discount across instance sizes and multiple Availability Zones within a Region. When purchase a Reserved Instance, AWS automatically applies the discount to other instance sizes within the same family based on the instance size footprint. It also applies the discount across multiple Availability Zones for enhanced resource distribution and fault tolerance.

**Spot Instances**
Bid on spare compute capacity at up to 90% off the On-Demand price, with the flexibility to be interrupted  when AWS reclaims the instance.

**Saving Plans**
Save up to 72% across a variety of instance types and services by committing to a consistent usage level for 1 or years.

- Good for: Predictable workload
  Offer discounts compared to On-demand rates in exchange for a commitment to use a specified amount of compute power over a 1 year or 3 year period. They provide flexible pricing for Amazon EC2, AWS Fargate, AWS Lambda and Amazon SageMaker AI usage.
https://aws.amazon.com/savingsplans/compute-pricing/

**Dedicated Hosts**
Reserve an entire physical server for exclusive use. This option offers full control and ideal for your exclusive use. This option offers full control and is ideal for workloads with strict security or licensing needs.

**Dedicated Instances**
Pay for instances running on hardware dedicated solely to account. This option provides isolation from other AWS customers.

![[Pasted image 20260507122457.png]]

| Dedicated Host                                                                                                                | Dedicated Instance                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Give an entire physical server for exclusive use, providing complete control over instance placement and resource allocation. | Which offer physical isolation from other AWS accounts while still benefiting from the flexibility and cost saving of shared infrastructure. |

# Scaling Amazon EC2
**Learning Objective**
- Recognize the concepts of scalability and elasticity and elasticity as they apply to AWS.
- Describe how AWS can help businesses adjust compute capacity based on varying demands.
**Scalability**
The ability of a system to handle an increased load by adding resources. Can scale up by adding more power to existing machines, or you can scale out by adding more machines. Scalability focuses on long-term capacity planning to make sure that the system can grow and accommodate more users or workloads as needed.
![[Pasted image 20260507212030.png]]

**Elasticity**

The ability to automatically scale resources up or down in response to real-time demand. A system can then rapidly adjust its resources, scaling out during periods of high demand and scaling in when the demand decreases. Elasticity provides cost efficiency and optimal resource usage at any given moment.
![[Pasted image 20260507212401.png]]
## Amazon EC2 Auto Scaling
With this service, maintain the desired amount of compute capacity for application by dynamically adjusting the number of EC2 instances based on demand.

**Minimum Capacity**
Defines the least number of EC2 instances required to keep the application running. This make sure that the system never scales below this threshold. It's the number of EC2 instances that launch immediately after created the Auto Scaling group.
![[Pasted image 20260507213228.png]]

**Desired Capacity**
The ideal number of instances needed to handle the current workload, which Auto Scaling aims it maintain. If do not specify the desired number of EC2 instances in an Auto Scaling group, the desired capacity defaults to minimum capacity.
![[Pasted image 20260507213628.png]]

**Maximum Capacity**
Sets an upper limit on the number of instances that can be launched, preventing over-scaling and controlling costs. Might configure the Auto Scaling group to scale out in response to increased demand.
![[Pasted image 20260507214324.png]]