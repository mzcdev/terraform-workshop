---
title: acm.tf
weight: 106
---

acm 디렉토리의 코드를 module 로 사용 합니다.

```hcl
module "domain" {
  source = "../acm"
  domain = var.domain_root
}
```
