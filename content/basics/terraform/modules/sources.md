---
title: Module Sources
weight: 101
---

모듈 블록의 소스 인수는 Terraform에게 원하는 하위 모듈의 소스 코드를 찾을 수있는 위치를 알려줍니다.

Terraform은 terraform init의 모듈 설치 단계에서 이를 사용하여 소스 코드를 로컬 디스크의 디렉토리에 다운로드하여 다른 Terraform 명령에서 사용할 수 있도록 합니다.

모듈 설치 프로그램은 아래 나열된 다양한 소스 유형에서 설치를 지원합니다.

### Local paths

로컬 경로 참조를 사용하면 단일 소스 리포지토리 내 구성의 일부를 가져올 수 있습니다.

```hcl
module "consul" {
  source = "./consul"
}
```

### GitHub

Terraform은 접두사가 없는 github.com URL을 인식하여 자동으로 Git 리포지토리 소스로 해석합니다.

```hcl
module "consul" {
  source = "github.com/hashicorp/example"
}
```

SSH를 통해 복제하려면 다음 형식을 사용하십시오.

```hcl
module "consul" {
  source = "git@github.com:hashicorp/example.git"
}
```

### Generic Git, Mercurial repositories

임의의 Git 리포지토리는 주소 앞에 특수한 `git::` 접두사를 붙여서 사용할 수 있습니다.
HTTPS 또는 SSH를 사용하려면 다음의 방법을 사용 하십시오.

```hcl
module "vpc" {
  source = "git::https://example.com/vpc.git"
}

module "storage" {
  source = "git::ssh://username@example.com/storage.git"
}
```

### S3 buckets

특수한 s3:: 접두어와 경로 스타일 S3 버킷 객체 URL을 사용하여 S3에 저장된 아카이브를 모듈 소스로 사용할 수 있습니다.

```hcl
module "consul" {
  source = "s3::https://s3-eu-west-1.amazonaws.com/examplecorp-terraform-modules/vpc.zip"
}
```
