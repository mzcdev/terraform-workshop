---
title: route53.tf
weight: 103
---

zone_id 를 획득 하기위해 data 타입으로 조회 합니다.

```hcl
data "aws_route53_zone" "this" {
  name = var.domain_root
}
```
