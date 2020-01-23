---
title: output.tf
weight: 108
---

결과를 출력 합니다.

```hcl
output "vpc_id" {
  value = aws_vpc.this.id
}

output "public_subnet_ids" {
  value = aws_subnet.public.*.id
}

output "private_subnet_ids" {
  value = aws_subnet.private.*.id
}

output "nat_gateway_ip" {
  value = aws_eip.private.public_ip
}
```
