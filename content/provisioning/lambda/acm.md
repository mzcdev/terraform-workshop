---
title: acm.tf
weight: 106
---

```hcl
module "domain" {
  source = "../acm"
  domain = var.domain_root
}
```
