---
title: output.tf
weight: 108
---

결과를 출력 합니다.

```hcl
output "url" {
  value = "https://${module.dev-lambda.domain}/demos"
}

output "invoke_url" {
  value = "${module.dev-lambda.invoke_url}"
}
```
