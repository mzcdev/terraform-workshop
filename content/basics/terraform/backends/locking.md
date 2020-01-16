---
title: Locking
weight: 102
---

백엔드는 상태를 저장하고 상태 잠금을위한 API를 제공합니다. 상태 잠금은 선택 사항입니다.

아래는 Amazon S3를 원격 상태 저장소로 사용하고, DynamoDB 를 잠금 기능으로 선언한 예시 코드입니다.

```hcl
terraform {
  backend "s3" {
    region         = "ap-northeast-2"
    bucket         = "terraform-workshop-seoul"
    key            = "vpc.tfstate"
    dynamodb_table = "terraform-workshop-seoul"
    encrypt        = true
  }
}
```
