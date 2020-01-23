---
title: output.tf
weight: 107
---

결과를 출력 합니다.

```hcl
output "id" {
  value = aws_instance.this.id
}

output "private_ip" {
  value = aws_instance.this.private_ip
}

output "public_ip" {
  value = aws_eip.this.public_ip
}
```
