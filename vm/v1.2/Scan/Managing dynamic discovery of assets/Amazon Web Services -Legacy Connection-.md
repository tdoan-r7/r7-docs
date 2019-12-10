---
title: "Amazon Web Services (Legacy Connection)"
excerpt: ""
---
The AWS legacy connection will only use the EC2 Describe capabilities, and the following code sample indicates how the policy should be defined: 
```
{
  "Version": "2012-10-17",
  "Statement": [{
     "Effect": "Allow",
     "Action": [
       "ec2:DescribeInstances",
       "ec2:DescribeImages",
       "ec2:DescribeAddresses"
     ],
     "Resource": "*"
  }]
}
```