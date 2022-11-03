# Disaster recovery

### What is Disaster recovery?

Disaster recovery is a plan that carries out when a disaster strikes. Such as one of the data centers gets hit by a tornado or catches on fire what is the plan from coming back from that. How will you quickly resume operations, how will you quickly stop losing devastating revenue, how will you quickly try and get your reputation back up?

### What is S3?

Stands for **Amazon Simple Storage Service** and it is a service that is designed as an online backup and archiving the data. 

Amazon S3 provides management features so that you can optimize, organize, and configure access to your data to meet your specific business, organizational, and compliance requirements.

### What are the benefits of S3?

- Scalable 
- High-speed
- Web based cloud storage service
- Data availability
- Security
- Performance

### Use cases of S3?

There are use cases such as data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

Examples
: hello this is an example

fsjsiodg
### How to set up s3 bucket connection

1. SSH into an instance that's not a db
2. Run `sudo apt-get install python3`
3. Run `sudo apt-get install python3-pip`
4. Run `sudo pip3 installl awscli`
5. Check python version by running `python --version`
6. If the version is below 3 run `alias python=python3` this should allow you to use python above 3
7. run `aws configure` and you should have 4 prompts 
   1. Access Key - enter your access key
   2. Secret Key - enter your secret key
   3. Region - enter aws region
   4. Output - enter output e.g `json`
8. if everything is working correctly. when you run `aws s3 ls` youu should see all the busckets 

---

<!-- ![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/s3diagram.png) -->

![Alt text](/images/s3diagram.png "s3 diagram")