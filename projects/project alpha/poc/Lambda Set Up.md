# Lambda Layer set up
1. add layer library to access postgres database
2. assign layer to only Python 3.8 not 3.7. Otherwise, you will see object not found when run library

# Attach to correct VPC and security group
![[Pasted image 20210125095527.png]]
VPC

[vpc-00a7f2ea88f37d846](https://us-east-2.console.aws.amazon.com/vpc/home?region=us-east-2#vpcs:search=vpc-00a7f2ea88f37d846) (172.27.172.0/22) | IM-Test-PERF-VPC-us-east-2

Subnets

-   [subnet-022b190f462b43324](https://us-east-2.console.aws.amazon.com/vpc/home?region=us-east-2#subnets:search=subnet-022b190f462b43324) (172.27.172.128/25) | us-east-2b, IM-Test-PERF-Lambda2b
-   [subnet-0aacff4a32fa78f6c](https://us-east-2.console.aws.amazon.com/vpc/home?region=us-east-2#subnets:search=subnet-0aacff4a32fa78f6c) (172.27.172.0/25) | us-east-2a, IM-Test-PERF-Lambda2a

Security groups

-   [sg-086b24192e86bc153](https://us-east-2.console.aws.amazon.com/vpc/home?region=us-east-2#SecurityGroups:search=sg-086b24192e86bc153) (IM-Test-PERF-ent-lambda-SG) | IM-Test-PERF-ent-lambda-SG


# [[POC Lambda Function code]]

# [[Factset set up]]
