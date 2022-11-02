# Step by step guide on how to migrate files into the VM

1. Once you have located the file you want to copy and have the directory to this file
2. You also have the directory to the destination
3. On your OS run a command that looks like this `scp -i eng130.pem -r /Users/subhaanadmin/end130_virtualisation/app/ ubuntu@ec2-52-208-34-131.eu-west-1.compute.amazonaws.com:/home/ubuntu`
4. It should now copy all the files from that directory
5. From the vm you can `ls` from the destination to see if the files are there 
   
![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/2-tier%20diagram.png)