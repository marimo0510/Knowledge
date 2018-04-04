
### emr  
	- DHCPからdomain-nameを受け取る必要あり  

### CSV出力
```
$ aws ec2 describe-instances --query 'Reservations[].Instances[].[
Tags[?Key==`Name`]|[0].Value,
InstanceType,
KeyName,
Platform,
Placement.AvailabilityZone,
SecurityGroups|[0].GroupName,
SecurityGroups|[1].GroupName,
SecurityGroups|[2].GroupName,
SecurityGroups|[3].GroupName,
SecurityGroups|[4].GroupName,
PrivateIpAddress,
PublicIpAddress,
IamInstanceProfile.Arn,
VpcId,
SubnetId
]' --output text | sed -e "s/\s/,/g" -e "s/None//g" -e "s/arn.*instance-profile\/\(.*,\)/\1/g" 
```