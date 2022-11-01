# Step by step guide on how to launch an Instance on AWS

- Once logged into AWS go to `EC2 dashboard`
- Click on `Instances`
- You should be able to see all the instances that are running at the time if there are any
- Click on the `Launch instances` button 
---
![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/Step1.png)

---
- Name the instance with best practices e,g `eng130_subhaan`
- Find the `ubuntu` version `18.04`
- Leave the instance type as default
- Key pair should be  `eng130` 
---   
![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/Step2.png)

---

-  In network settings a security group has been made called `eng130_subhaan_sg` 

---
![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/Step3.png)

---

-  Configure storage could just be `8gb`
-  Have a look through the summary to see if everything is correct
-  Press `Launch instance` 
-  you will now see it in the `instances` tab 
---

![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/Step4.png)

---

# How to connect to the Instance using Terminal

- Tick the Instance you want to connect to `eng130_subhaan`
- Go to `SSH client` 
- Copy the example given e.g `ssh -i "eng130.pem" ubuntu@ec2-34-245-4-146.eu-west-1.compute.amazonaws.com` 
- Go to your terminal and run this command `cd ~/.ssh`
- Then paste the example you copied
- You will now be connected to the VM