---
title: backend.tf
weight: 101
---

`State` 정보를 저장하기 위해 `backend` 설정을 해줍니다.

`Provider` 는 AWS 를 사용 합니다.

```hcl
terraform {
  backend "s3" {
    region         = "ap-northeast-2"
    bucket         = "terraform-workshop-seoul"
    key            = "vpc-demo.tfstate"
    dynamodb_table = "terraform-workshop-seoul"
    encrypt        = true
  }
}

provider "aws" {
  region = var.region
}
```
