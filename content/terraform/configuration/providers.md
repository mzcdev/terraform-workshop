---
title: Providers
weight: 312
---

자원(Resource)은 Terraform 언어의 기본 구성이지만 자원의 동작은 연관된 자원 유형에 의존하며 이러한 유형은 제공자(Provider)에 의해 정의됩니다.

각 제공자는 이름 지정된 자원 유형 세트를 제공하고 각 자원 유형에 대해 허용되는 인수, 내보내는 속성 및 해당 유형의 자원 변경 사항이 실제로 원격 API에 적용되는 방법을 정의합니다.

사용 가능한 대부분의 공급자는 하나의 클라우드 또는 온-프레미스 인프라 플랫폼에 해당하며 해당 플랫폼의 각 기능에 해당하는 리소스 유형을 제공합니다.

공급자는 일반적으로 엔드 포인트 URL, 리전, 인증 설정 등을 지정하기 위해 자체 구성이 필요합니다. 동일한 제공자에 속하는 모든 자원 유형은 동일한 구성을 공유하므로 모든 자원 선언에서이 공통 정보를 반복 할 필요가 없습니다.

### Provider Configuration

`provider` 블록을 사용 하여 설정 합니다.

```hcl
provider "aws" {
  region = var.region
}
```

```hcl
provider "google" {
  region  = var.region
  project = var.project
}
```

### Initialization

새 제공자가 명시 적으로 제공자 블록을 통해 또는 해당 제공자의 자원을 추가하여 구성에 추가 될 때마다 Terraform은 제공자를 사용하기 전에 제공자를 초기화해야합니다. 초기화는 나중에 실행할 수 있도록 공급자의 플러그인을 다운로드하여 설치합니다.

```bash
terraform init
```
