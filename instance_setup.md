# Step by step guide on how to launch an Instance on AWS

1. Once logged into AWS go to `EC2 dashboard`
2. Click on `Instances`
3. You should be able to see all the instances that are running at the time if there are any
4. Click on the `Launch instances` button 
---
![alt text](../eng130-aws-intro/images/Step1.png)

---

5. Name the instance with best practices e,g `eng130_subhaan`
6. Find the `ubuntu` version `18.04`
7. Leave the instance type as default
8. Key pair should be  `eng130` 
---   
![alt text](../eng130-aws-intro/images/Step2.png)

---

9.  In network settings a security group has been made called `eng130_subhaan_sg` 

---
![alt text](../eng130-aws-intro/images/Step3.png)

---

10. Configure storage could just be `8gb`
11. Have a look through the summary to see if everything is correct
12. Press `Launch instance` 
13. you will now see it in the `instances` tab 
---

![alt text](../eng130-aws-intro/images/Step4.png)

---

# How to connect to the Instance using Terminal

1. Tick the Instance you want to connect to `eng130_subhaan`
2. Go to `SSH client` 
3. Copy the example given e.g `ssh -i "eng130.pem" ubuntu@ec2-34-245-4-146.eu-west-1.compute.amazonaws.com` 
4. Go to your terminal and run this command `cd ~/.ssh`
5. Then paste the example you copied
6. You will now be connected to the VM