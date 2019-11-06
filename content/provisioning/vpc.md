---
title: VPC
weight: 35
---

> Public subnet 과 Private subnet 을 포함한 VPC 를 생성 합니다.

![VPC](../../provisioning/images/terraform_vpc_ach.png)

> 다음 파일에서 **terraform-workshop-seoul** 을 생성한 버켓명으로 변경해줍니다.

```
# export BUCKET="terraform-nalbam-seoul"

cd terraform-env-workshop/vpc

sed -i "s/terraform-workshop-seoul/${BUCKET}/g" ./main.tf
sed -i "s/terraform-workshop-seoul/${BUCKET}/g" ./variable.tf
```

> Terraform 명령으로 생성 합니다.

```
terraform init
terraform plan
terraform apply
```

> 다음과 같은 메세지가 출력 되면 성공 입니다.

```
Apply complete! Resources: x added, 0 changed, 0 destroyed.

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
