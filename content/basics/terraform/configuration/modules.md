---
title: Modules
weight: 317
---

Module은 함께 사용되는 여러 리소스의 컨테이너입니다.

모든 Terraform 구성에는 기본 작업 디렉토리의 .tf 파일에 정의 된 리소스로 구성된 루트 모듈이라고하는 하나 이상의 모듈이 있습니다.

모듈은 다른 모듈을 호출 할 수 있으며, 이를 통해 하위 모듈의 리소스를 간결하게 구성에 포함시킬 수 있습니다. 동일한 구성 내에서 또는 별도의 구성으로 모듈을 여러 번 호출하여 리소스 구성을 패키지화하고 재사용 할 수 있습니다.

### Calling a Child Module

`module` 블록을 사용 하여 설정 합니다.

```
module "servers" {
  source = "./sub_module"

  servers = 5
}
```

module 키워드 바로 뒤에있는 레이블은 로컬 이름이며 호출 모듈은이 모듈 인스턴스를 참조하는 데 사용할 수 있습니다.

모든 모듈에는 Terraform CLI에 의해 정의 된 메타 인수 인 `source` 인수가 필요합니다. 그 값은 모듈 구성 파일의 로컬 디렉토리에 대한 경로이거나 Terraform이 다운로드하여 사용해야하는 원격 모듈 소스입니다.

```
module "vpc" {
  source = "github.com/nalbam/terraform-aws-vpc?ref=v0.12.8"

  region = var.region
  name   = var.name
}
```

깃헙 주소 `https://github.com/nalbam/terraform-aws-vpc` 에서 `v0.12.8` Tag 를 지정하여 사용 할 수 있습니다.

### Accessing Module Output Values

모듈에 정의 된 리소스는 캡슐화되므로 호출 모듈은 해당 속성에 직접 액세스 할 수 없습니다. 그러나 자식 모듈은 출력 값을 선언하여 호출 모듈이 액세스 할 특정 값을 선택적으로 내보낼 수 있습니다.

```
resource "aws_elb" "example" {
  # ...

  instances = module.servers.instance_ids
}
```
