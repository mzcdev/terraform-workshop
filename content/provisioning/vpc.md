---
title: VPC
weight: 33
---

> Public subnet 과 Private subnet 을 포함한 VPC 를 생성 합니다.

![Success](../../terraform/images/terraform_vpc_ach.png)

> Terraform 명령으로 생성 합니다.

```
cd terraform-env/vpc

terraform init
terraform plan
terraform apply
```

> 다음과 같은 메세지가 출력 되면 성공 입니다.

```
Apply complete! Resources: 0 added, 0 changed, 0 destroyed.

Outputs:

nat_ip = [
  "52.78.13.15",
]
private_subnet_cidr = [
  "10.15.4.0/24",
  "10.15.5.0/24",
  "10.15.6.0/24",
]
private_subnet_ids = [
  "subnet-034abbc6xc10634ad",
  "subnet-0944x61ec8c2f8f93",
  "subnet-06b7d51d44537x626",
]
public_subnet_cidr = [
  "10.15.1.0/24",
  "10.15.2.0/24",
  "10.15.3.0/24",
]
public_subnet_ids = [
  "subnet-092938d936610xbfe",
  "subnet-026b23axc4b257e42",
  "subnet-0xfe713b44d028898",
]
vpc_id = vpc-0fxb2037axdc5b059
```
