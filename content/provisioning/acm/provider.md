---
title: provider.tf
weight: 101
---

`us-east-1` 리전을 사용 하도록 합니다.

```hcl
provider "aws" {
  region = var.region
}
```
