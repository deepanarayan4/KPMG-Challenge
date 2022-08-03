# KPMG-Challenge

Challenge-1:

Create a 3-Tier Architecture via AWS CloudFormation

Below Approach is as per my understanding on 3-tier architecture. Since in my current project we use AWS CFT for deploying the infrastructure, I have chosen CloudFormation templates to deploy the resources.

Three Tier Architecture consists of 3 layers/tiers:
Web Tier: Main purpose to is display the information to and collect information from the user
App Tier: Main purpose to process the user inputs.
Database Tier: It is a backend tier for web application. This is place where the information is stored and managed.

Step 1: CFT for VPC, RT, IGW,2 public subnets, RT for public subnets, scaling policy for public subnets, Security Group for instance, ASG for public sunbets.

    Steps for CFT Creation in console:
     1. Login to AWS console--> Select service Cloudformation---Click in Create stack.
     2.Select tenplate Ready option--> Upload 3tier.yaml file--> Next
     3.Provide the StackName: WebAPP_Kpmg
     4. Assign the IAM role--> Create Stack

Step 2: CFT for RDS Data base creation, Follow same Step-1 to create stack in aws console except the stack name. StackName: RDS_Kpmg

Step 3: CFT for NAT gateway to route the traffic.
Follow same Step-1 to create stack in aws console except the stack name and few parameters mentioned below
    1. StackName: NAT_Kpmg
    2. Public Subnet: ex:10.0.16.0/20
    3. Private Route Table: Take it from VPC-->Route Table-->Route Table ID Number
    4. Public Network ACL: Take if from VPC-->Network ACLs-->Take Network ACL ID number

Testing:

Try to ping private databse instance ip address from public web instance.
Access the DNS record of Application Web server Ec2 instance from Browser and the message should print "Second Round Evaluation from KPMG"
