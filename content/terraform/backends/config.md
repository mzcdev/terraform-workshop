---
title: Backend Configuration
weight: 101
---

백엔드는 terraform 섹션의 Terraform 파일에서 직접 구성됩니다. 백엔드를 구성한 후에는 `terraform init` 을 해야합니다.

```hcl
terraform {
  backend "s3" {
    region = "ap-northeast-2"
    bucket = "terraform-workshop-mzcdev"
    key    = "vpc.tfstate"
  }
}
```

{{% notice tip %}}
백엔드는 하나만 지정할 수 있습니다.
{{% /notice %}}
