---
title: result
weight: 199
---

Terraform 명령으로 생성 합니다.

```bash
terraform init
terraform plan
terraform apply
```

다음과 같은 메세지가 출력 되면 성공 입니다.

```text
Apply complete! Resources: x added, 0 changed, 0 destroyed.

Outputs:

nat_gateway_ip = [
  "52.78.13.15",
]
private_subnet_ids = [
  "subnet-034abbc6xc10634ad",
  "subnet-0944x61ec8c2f8f93",
  "subnet-06b7d51d44537x626",
]
public_subnet_ids = [
  "subnet-092938d936610xbfe",
  "subnet-026b23axc4b257e42",
  "subnet-0xfe713b44d028898",
]
vpc_id = "vpc-0fxb2037axdc5b059"
```
