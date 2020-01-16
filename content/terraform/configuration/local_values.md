---
title: Local Values
weight: 315
---

Local Value는 이름을 표현식에 지정하여 모듈 내에서 반복하지 않고 여러 번 사용할 수 있습니다.

### Declaring a Local Value

`locals` 블록을 사용 하여 설정 합니다.

```hcl
locals {
  service_name = "forum"
  owner        = "Community Team"
}
```

간단한 상수 이거나, 다른 모듈 또는 다른 리소스 값을 반환하거나, 복잡한 표현식도 가능 합니다.

```hcl
locals {
  # 두개의 인스턴스의 ID List를 반환 합니다.
  instance_ids = concat(
    aws_instance.blue.*.id,
    aws_instance.green.*.id,
  )
}

locals {
  # 모든 자원에서 사용할 공통 태그
  common_tags = {
    Service = local.service_name
    Owner   = local.owner
  }
}


locals {
  # vpc 를 만들도록 설정 했으면 생성된 리소스에서 id 를 가져오고,
  # 만들지 않 도록 설정 헸으면 변수에서 가져 온다.
  vpc_id = var.create_vpc ? element(concat(aws_vpc.this.*.id, [""]), 0) : var.vpc_id
}
```
