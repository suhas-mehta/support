Private Deployment
==================

A private deployment of Falkonry can be made into an Infrastructure-as-a-Service provider
such as Microsoft Azure or AWS. It is also possible to provide a private deployment of
Falkonry in your own data center or rack.

If you would prefer to manage the service yourself, either on your private cloud or your 
own servers, the self-managed deployment option is also available.

Requirements for Private Deployment
----------------------------------------
In order to support your exclusive Falkonry deployment, you will need to meet the following
system requirements:

- Network - internet access and outbound access
- Hardware - min. 2 cores and 8 GB RAM, recommended 4 cores and 16 GB RAM
- Supported Operating Systems 

  - Ubuntu Linux
  - Google Linux
  - Redhat Enterprise Linux (6.4 or later)
  
- Storage 

  - Temporary storage is used on the virtual machines to keep internal state. 
  - External stable memory will be required to support queries on pipelines over the long 
    term. This memory can be on online block storage and mounted as a file system on 
    the computer where Falkonry is allowed to store the input data as well as its assessments.