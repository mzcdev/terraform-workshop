---
title: eip.tf
weight: 106
---

탄력적 IP 를 생성하여 인스턴스에 연결 합니다.

```hcl
resource "aws_eip" "this" {
  instance = aws_instance.this.id

  vpc = true

  tags = {
    Name = var.name
  }
}
```
