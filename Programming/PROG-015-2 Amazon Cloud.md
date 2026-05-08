# Introduction
**Lesson Objective**
- Describe the client-server model at a fundamental level.
## Client-server model
>[!note] Coffee shop
>![[Pasted image 20260506233338.png]]
>1. Morgan be the server, the barista. Alan be the client.
>2. He make request with permission, the server responds to that request.
>3. Morgan represents the server part of the client-server model.
>4. The user made a request to Morgan. She validated that the request was legitimate.
>5. When need more resources, just provision them right then and there. Deprovision the resources when you not need.

# What is Cloud Computing
- Define Cloud computing
- Describe and differentiate between cloud deployment types
>[!note] Definition
>On-demand delivery of IT resources over the internet with pay as you go pricing.
>- **On-demand delivery**
>  means that customers can access computing resources such as storage or compute power, within seconds and as needed. Users can scale their resource usage up or down based on current requirement without lengthy provisioning processes.
>- **IT resources**
>  Highlights the wide array of IT assets in the cloud-computing space. These resources include server, storage, solutions, databases, networking components, AI and ML tools. Customer can use these resources to build, deploy and manage applications and services though the cloud infrastructure.
>- **Over the internet**
>  That delivers IT resources through internet connectivity. Means that users access and use these resources through web-based services rather than maintaining local hardware or software. Acts as the conduit which provides remote access to compute power, storage, and applications from anywhere in the world.
>- **With pay-as-you-go pricing**
>  Users pay only for the resources they actually consume, rather than committing to fixed, long-term contracts. This usage-based pricing model offers cost efficiency and financial flexibility.

## Cloud deployment types
- Cloud-based deployment
  Flexibility to migrate existing resources to the cloud, design and build new applications within the cloud environment or a combination of both.
  
  A company might migrate data resources to the cloud then develop an application comprised of virtual servers, databases and networking components entirely hosted in the cloud. 
- On-premises
  Same as legacy IT infrastructure while using application management and virtualization technologies to try increasing resource utilization.
- Hybrid
  This approach is ideal for situations where legacy application must remain on premises due to maintenance preferences or regulatory requirement.
  
  A company might choose to retain certain regulated legacy application on-premises while using cloud services for advanced data processing and analytics.
## Advantage
- Trade fixed expense for variable expense
  Businesses  can transition from fixed investment to variable costs. With variable costs, customer expenses are better aligned with actual usage, thus creating more financial flexibility.
- Benefit from massive economies of scale
  Can be used by many organizations, from small startups to major corporations. Businesses big and small can access advanced technologies that were previously only accessible to large enterprises.
- Stop guessing capacity
  Can dynamically scale AWS Cloud resources up or down based on real-time demand. This means businesses can achieve optimal performance without provisioning more or less infrastructure than they need.
- Increase speed and agility
  Accelerating time to market and facilitating time to market and facilitating quicker responses to changing business needs and market conditions.
- Stop spending money to run and maintain data centres
  Customer aren't required to spend time and money on utilities and ongoing maintenance. With AWS taking care of the physical infrastructure of the cloud, customer resources can be reallocated to more strategies initiatives.
- Go global in minutes
  Businesses don't need to set up their own infrastructure to expand internationally. AWS provides a robust global infrastructure that customers can use to deploy applications and services across multiple areas in minutes.

# AWS Regions and Availability Zones
- Consists of physical locations around the world that contain group of data centers.
![[Pasted image 20260507091632.png]]
1. Physical locations around the world that contain groups of data centres. These groups of data centers are called Availability Zones. Each AWS Region consists of a minimum of 3 physical separate Availability Zones within a geographic area.
2. Availability Zones consists of 1 or more data centers with reductant power, networking and connectivity. Regions and Availability Zones are designed to provide low-latency, fault- tolerant access to services for users within a given area.
## Achieving high availability with AWS Global Infrastructure
- If 1 AZ encounters an outage, business applications will continue operate without interruption. With this approach of redundancy and resource isolation, AWS customers can achieve the benefit of high availability and fault tolerance.
# AWS Shared Responsibility Model
**Lesson Objective**
- Describe and differentiate between customer responsibilities, AWS responsibilities and shared responsibilities in the AWS Cloud.
- Describe the components of the AWS Shared Responsibility Model.

![[Pasted image 20260507093306.png]]

1. **Customer Responsibility**
   Responsible for managing security requirements for their data including which data they store on AWS and who has access to that data. Customers also control how access to the data is granted, managed and revoked.
2. **Customer on AWS Responsibility**
   Server-side encryption, network traffic protection, platform and application management and OS, network and firewall configuration vary by service in terms of who is responsible for these items.

3. **AWS responsibility**
   Protecting the infrastructure that runs all of the services offered in the AWS Cloud. This infrastructure is composed of the hardware, software, networking and facilities that run AWS Cloud services.
# Applying Cloud Concepts to Real Life Use Cases
**Lesson Objective**
- Explain how fundamental cloud concepts such as the AWS Global infrastructure and AWS Shared Responsibility Model, work together to form real-world business solutions.
![[Pasted image 20260507094713.png]]
1. Ecommerce company expansion
   The company wants to expand to global locations. However, the further the computing infrastructure is from their customers, the longer the latency. The company decides to expand to global AWS Regions to better reach their global customers.
2. Global expansion 1: Ireland
   Deploying in multiple Regions increases high availability. The company increases fault-tolerance and high availability Zones in this Region.
   Company does not need to worry about securing the physical infrastructure is an AWS responsibility. The company can instead focus on securing and encrypting their data within their cloud resources.
3. Global expansion 2: Singapore
   The company has a significant customer base in Asia too. They deploy resources to Region in Singapore.
   Rather than having to set up physical infrastructure at an international scale which can take months or years, the company used AS to deploy global operations within a matter of minutes.