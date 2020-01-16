---
title: State Locking
weight: 103
---

백엔드에서 지원하는 경우 Terraform은 상태를 기록 할 수있는 모든 작업에 대해 상태를 잠급니다. 이렇게하면 다른 사람이 잠금을 획득하여 잠재적으로 상태를 손상시킬 수 없습니다.

상태 잠금은 상태를 기록 할 수있는 모든 작업에서 자동으로 발생합니다. `-lock` 플래그를 사용하여 대부분의 명령에 대해 상태 잠금을 비활성화 할 수 있지만 권장되지는 않습니다.

### Example

```hcl
terraform {
  backend "s3" {
    region         = "ap-northeast-2"
    bucket         = "terraform-mz-seoul"
    key            = "vpc-demo.tfstate"
    dynamodb_table = "terraform-mz-seoul"
    encrypt        = true
  }
}
```

![graph](../../state/images/locking.png)
