---
title: Backends
weight: 370
---

Terraform의 `Backend`는 `State`가 로드되는 방식과 apply와 같은 작업이 실행되는 방식을 결정합니다.

### Benefits of backends

* 팀 협업: 상태를 원격 저장하고, 실행중 일때 상태를 잠금으로 보호하여 손상을 방지 할수 있습니다.

* 중요한 정보 유지: 정의 하지 않을 경우 메모리에만 저장됩니다. Amazon S3와 같이 원격지에 저장 할수 있습니다.

* 원격 운영: 대규모의 인프라의 생성 또는 변경은 작업 시간이 오래 걸릴 수 있습니다. 일부 백엔드는 원격작업을 지원하여 작업을 원격에서 유지 할수 있습니다. 원격 상태 저장소와 잠금 기능을 같이 사용 하면 팀 협업에 도움이 됩니다.

아래는 Amazon S3를 원격 상태 저장소로 사용하고, DynamoDB 를 잠금 기능으로 선언한 예시 코드입니다.

```
terraform {
  backend "s3" {
    region         = "ap-northeast-2"
    bucket         = "terraform-workshop-seoul"
    key            = "vpc.tfstate"
    dynamodb_table = "terraform-workshop-seoul"
    encrypt        = true
  }
  required_version = ">= 0.12"
}
```

더 많은 정보를 확인 하시려면 아래 링크를 참고 하세요.

* https://www.terraform.io/docs/backends/index.html
