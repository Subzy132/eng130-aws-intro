# AWS Intro

---

### What is cloud computing? Why? Benefits? 

It essentially allows an organisation to use services such a servers, storage, databases, networking, software, analytics and intelligence. But in this case it is over the internet so no local device is needed. 

Cloud computing is good because it offers faster innovation, flexible resources and works with economies of any scale. 

The benefits are that it is usualy very cost effective as you are only paying for the cloud service. You will be able to run your infrastructure more efficiently and scale your business whenever needed. 

- Ease of use
- Flexibility 
- Robustness
- Cost
- 

---

### What is AWS? Who is using it and why?

AWS is Amazon Web Services and it is THE world's most used cloud platofrm. That has more than 200 data centres globally. It offers it's services to the larger companies and also th e start ups. 

companies like `netlfix`, `expedia` and `slack` use AWS because it lowers costs and is more agile and the company are able to innovate faster.


---

![alt text](https://www.computerweekly.com/rms/computerweekly/photogalleries/241360/2357_20_the-difference-between-saas-paas-and-iaas.jpg)

---
### CAP-EX vs OP-EX

- CAP-EX = Capital expenditures are major purchases a company makes that are designed to be used over the long term.
- OP-EX = Operating expenses are the day-to-day expenses a company incurs to keep its business operational.

![alt text](../images/CAPEX.png)
---

### What is On-Prem? 

An on-premises data center is a group of servers that you privately own and control. Traditional cloud computing (as opposed to hybrid or private cloud computing models) involves leasing data center resources from a third-party service provider.

### What is aws diagram

![''](https://coursereport-production.imgix.net/rich/rich_files/rich_files/5032/original/what-is-aws-learn-amazon-web-services-infographic.png?auto=compress%2Cformat&w=3038&h=)

---
### How to set up s3 bucket

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

![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/s3diagram.png)