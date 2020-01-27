---
title: output.tf
weight: 108
---

결과를 출력 합니다.

```hcl
output "url" {
  value = "https://${var.domain_name}/demos"
}

output "invoke_url" {
  value = aws_api_gateway_deployment.default.invoke_url
}
```
