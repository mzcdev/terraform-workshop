---
title: Instance
weight: 10
---

기본 설정으로 Instance 하나를 생성 합니다.

```hcl
resource "aws_instance" "this" {
  ami           = "ami-0bea7fd38fabe821a"
  instance_type = "t2.micro"

  tags = {
    Name = var.name
  }
}

output "id" {
  value = aws_instance.this.id
}
```

Terraform 명령으로 생성 합니다.

```bash
terraform init
terraform plan
terraform apply
```

다음과 같은 메세지가 출력 되면 성공 입니다.

```text
Apply complete! Resources: x added, 0 changed, 0 destroyed.

Outputs:

id = "i-0661eb15x9b3e2f0b"
```
