---
title: Output Values
weight: 314
---

Output Value는 Terraform 모듈의 반환 값과 유사하며 여러 용도로 사용됩니다.

### Declaring an Output Value

`output` 블록을 사용 하여 설정 합니다.

```
output "private_ip" {
  value = aws_instance.server.private_ip
}
```

`value` 인수는 결과가 사용자에게 리턴되는 표현식을 사용합니다.

### Accessing Child Module Outputs

상위 모듈에서 하위 모듈의 출력은 `module.<MODULE NAME>.<OUTPUT NAME>`로 표현할 수 있습니다. 예를 들어, server라는 하위 모듈이 private_ip라는 출력을 선언 한 경우 해당 값에 `module.server.private_ip`로 액세스 할 수 있습니다.
