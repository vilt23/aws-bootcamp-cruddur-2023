# Week 0 — Billing and Architecture

### Recreation of diagram using LucidChart

#### I have created the logical diagram using LucidChart that you can find clicking the following link [Lucid Chart Link](https://lucid.app/lucidchart/06a59b70-2248-4d22-b842-cc56a1f510c6/edit?viewport_loc=28%2C272%2C1342%2C628%2C0_0&invitationId=inv_0c63ccfd-7ee3-4ca6-b4b6-9a5bf6eac855)


![PNG picture of the LucidChart Diagram](assets/Week%200%20-%20Diagram.png)



### Installation of AWS CLI in Gitpod

#### Following the instructions i have downloaded the package, unzip and install the AWS CLI 
You will find the link to the gitpo.yml script here [AWS CLI installation script](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/.gitpod.yml)
And run the command get caller identity as a demo
![get caller identity cli demo](assets/Week%200%20-%20Caller%20Identity.png)

### Creation of budget using CLI
#### I created the create a budget of $10 by running the budget.json script saved in the aws/json folder in the CLI. [Budget.json script](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/aws/json/budget.json) and [notify subscriber script](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/aws/json/notifications-with-subscribers.json)
![budget.json script](assets/Week%200%20-%20Budget.png) 

### Creation of Alarm and SNS topics
#### I have also created the an SNS topic and an alarm to notify me when my sending are approaching the $10 threshold to prevent overspending using the same method as the budget creation. Find the link to the script here [Alarm script](https://github.com/vilt23/aws-bootcamp-cruddur-2023/blob/main/aws/json/alarm_config.json)
![alarm in console](assets/Week%200%20-%20Alarm.png)
![SNS topic in console](assets/Week%200%20-%20SNS%20topics.png)

### Homework Challenges
#### As homework challenge, i am proposing some modification of the diagram to improve security and reliability.
First i place a Web Application Firewall (WAF) before the load balancer to protect the application against attack. I have also place the front end and the back end containers inside autoscaling groups to be sure they will be able to handle traffic variations. I have also use some SQSs to decouple the app and prevent data loss while auto scaling groups are scaling up. Find the link to the lucidChart diagram here. [Homework Challenge LucidChart Diagram](https://lucid.app/lucidchart/7d11af48-bdf5-4e0a-82b6-83defb230f24/edit?viewport_loc=158%2C32%2C1615%2C991%2C0_0&invitationId=inv_f7d1a6c4-3267-42b8-aea1-526022eb8780)
![Homework Challenge LucidChart Diagram](assets/Week%200%20-%20Week%20Challenge%20Diagram%20.png)
