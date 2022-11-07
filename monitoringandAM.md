# Monitoring and Alert Management

### Monitoring

Monitoring is the ability to be able to obtain control over your AWS ecosystem. With monitoring you are able to see what is going on and if there are any issues. You are able to set up alarms and get Notifications as to where the issue lies and then be able to fix them easily.  

Amazon Web Services (AWS) monitoring scans your AWS resources and applications, collecting data to ensure everything is operating smoothly and securely. Monitoring your AWS infrastructure helps identify vulnerabilities and issues, predict performance and optimize configurations. This practice relies on various tools and services to collect, analyze and present data insights.

![Alt text](/images/Cloudwatch.png "s3 diagram")
![Alt text](/images/Alarm.png "s3 diagram")


### What is SNS?

Simple Notification Service is a service provided by Amazon that allows the AWS to send you a notification, this being an email for any sort of issue that occurs. You first need to subscribe to these emails and then you need to set up the alarms to alert you for whatever occasion you want. 

In my example I set up an alarm to alert me when my CPU usage goes above 20%. The monitoring system will then detect this and then the SNS will send you an email explaining this. 

![Alt text](/images/SNS.png "s3 diagram")

### How to set up Alarm:

1. Have an `EC2 Instance` setup 
2. Go to the Instance and the press `Monitoring` and click the button that says `Add to Dashboard`
3. Create a dashboard if you dont have one already
4. On the Left hand side it should say `Alarms` click on `All alarms`
5. Then click on `Create alarm`
6. A pop up will appear allowing you to pick a metric. 
7. Once you have picked a metric you press `Add metric`
8. You can now pick the configuration.
9. Click `next`
10. Pick the trigger and then `create a new topic`. This will be your email.
11. Name the alarm and then click `create alarm`
12. Now subcribe to the emails and you have the SNS setup