# aws-ssm-connectivity-for-ipv6-instances-and-private-instances

## AWS Systems Manager

Resources managed by AWS Systems Manager must have IPv4 connectivity to Systems Manager’s endpoints. For example, to connect to an EC2 instance using Systems Manager Session Manager, the instance must be running dual-stack and must have an IPv4 connectivity to the internet or AWS PrivateLink VPC endpoint. Similarly, on-premises resources must also be in dual-stack network mode.

## Creating VPC Endpoints for System manager:
In the first step of this procedure Create a two required seperate vpc endpoint to connect system manger Run Command **com.amazonaws.region.ssm** and **com.amazonaws.region.ec2messages** and **com.amazonaws.region.ssmmessages** (optional - for session-manager connectivity)
### Prerequistes:
•		VPC with ipv6 enabled
•		Subnet which is associated in private route-table or disabled auto-enabled public ipv4

### Steps
1.	Separate security group for vpc-endpoint with ingress port 443 and associated by vpc cidr range
2.	Create the VPC endpoint in VPC console
3.	Give the name of the endpoint (eg: ssin-vpc-endpoint-ssm)
4.	Service Category – select AWS services
5.	Services – select the services for system manager “com.amazonaws.region.ssm”
6.	Select the respective VPC in the VPC section
7.	Select the subnet for the respective availability zone where the ec2 instance located
8.	Select the above created security group for vpc endpoint
9.	Policy – set default as full access and Create Endpoint
10.	Do the above same steps for “com.amazonaws.region.ec2messages”
	
![image](https://github.com/praveensivakumar1998/aws-ssm-connectivity-for-ipv6-instances-and-private-instances/assets/108512714/59cd125a-4712-435c-912a-c83e01b7acf7)

Now you can able to run the scripts in System Manager – Run command and Fleet manager for the respective ipv6 or Private machines 
