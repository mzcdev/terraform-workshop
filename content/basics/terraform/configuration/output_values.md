---
title: Output Values
weight: 314
---

Output Value는 Terraform 모듈의 반환 값과 유사하며 여러 용도로 사용됩니다.

### Declaring an Output Value

`output` 블록을 사용 하여 설정 합니다.

```hcl
output "private_ip" {
  value       = aws_instance.server.private_ip
  description = "The private IP address of the main server instance."

  depends_on = [
    aws_security_group_rule.local_access,
  ]
}

output "db_password" {
  value       = aws_db_instance.db.password
  description = "The password for logging in to the database."
  sensitive   = true
}
```

`value` 인수는 결과가 사용자에게 리턴되는 표현식을 사용합니다.

`description` 인수를 사용하여 각 값의 목적을 간단히 설명 할 수 있습니다.

`sensitive` 출럭값을 마스킹 할 수 있습니다.

`depends_on` 출력 값은 모듈에서 데이터를 전달하는 수단 일 뿐이므로 일반적으로 종속성 그래프에서 다른 노드와의 관계에 대해 걱정할 필요가 없습니다. 그러나 상위 모듈이 하위 모듈 중 하나에서 내 보낸 출력 값에 액세스 할 때 해당 출력 값의 종속성을 통해 Terraform은 다른 모듈에 정의 된 리소스 간의 종속성을 올바르게 결정할 수 있습니다.

### Accessing Child Module Outputs

상위 모듈에서 하위 모듈의 출력은 `module.<MODULE NAME>.<OUTPUT NAME>`로 표현할 수 있습니다. 예를 들어, server라는 하위 모듈이 private_ip라는 출력을 선언 한 경우 해당 값에 `module.server.private_ip`로 액세스 할 수 있습니다.
