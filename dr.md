# Disaster recovery

### What is Disaster recovery?

Disaster recovery is a plan that carries out when a disaster strikes. Such as one of the data centers gets hit by a tornado or catches on fire what is the plan from coming back from that. How will you quickly resume operations, how will you quickly stop losing devastating revenue, how will you quickly try and get your reputation back up?

### Why It's Important

- To minimize interruptions to normal operations.
- To limit the extent of disruption and damage.
- To minimize the economic impact of the interruption.
- To establish alternative means of operation in advance.
- To train personnel with emergency procedures.
- To provide for smooth and rapid restoration of service.

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
- Cost effectiveness

### Use cases of S3?

There are use cases such as data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

Examples

- Backup file system: This is the most popular use case. to be able to back up all the files to a secure place. 
- Infrequent Access
- Data Archiving
- Disaster Recovery
- Data Lake Storage
- ### How to set up s3 bucket connection

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


Here are some commands to try on the bucket

- `aws s3 mb s3://{bucket name}` to make bucket
- `aws s3 cp` to copy files
- `aws s3 rm` to delete files
- `aws s3 rb` to remove bucket


---

<!-- ![alt text](https://github.com/Subzy132/eng130-aws-intro/blob/main/images/s3diagram.png) -->

![Alt text](/images/s3diagram.png "s3 diagram")

### How to automate s3 bucket commands

I have made a script to add to the VM that will run in the python Environment: 

```python
import logging
import boto3
from botocore.exceptions import ClientError
import os
import sys 

def create_bucket(bucket_name, region='eu-west-1'):

    try:
        s3_client = boto3.client('s3', region_name=region)
        location = {'LocationConstraint': region}
        s3_client.create_bucket(Bucket=bucket_name,
                                CreateBucketConfiguration=location)
    except ClientError as e:
        logging.error(e)
        return False
    return True

def upload_file(file_name, bucket, object_name=None):
    if object_name is None:
        object_name = file_name

    # Upload the file
    s3_client = boto3.client('s3')
    try:
        response = s3_client.upload_file(file_name, bucket, object_name)
    except ClientError as e:
        logging.error(e)
        return False
    return True

def download_file(bucket_name, object_name, file_name):
    s3 = boto3.client('s3')
    s3.download_file(bucket_name, object_name, file_name)

def delete_bucket(bucket_name, region="eu-west-1"):
    s3 = boto3.resource('s3', region_name=region)
    s3.Bucket(bucket_name).delete()

def delete_file(bucket, object, region="eu-west-1"):
    s3 = boto3.client('s3', region_name=region)
    s3.delete_object(Bucket=bucket, Key=object)   

# create_bucket('eng130-subhaan', 'eu-west-1') 

if __name__ == "__main__":

    args = sys.argv

    globals()[args[1]](*args[2:])
```