---
title: Instance
weight: 92
---

Terraform 명령으로 삭제 합니다.

```bash
cd terraform-env-workshop/instance

terraform destroy
```

```
aws_instance.this: Refreshing state... [id=i-0390f0e077a519e15]

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  - destroy

Terraform will perform the following actions:

  # aws_instance.this will be destroyed
  - resource "aws_instance" "this" {
      ....
    }

Plan: 0 to add, 0 to change, 1 to destroy.

Do you really want to destroy all resources?
  Terraform will destroy all your managed infrastructure, as shown above.
  There is no undo. Only 'yes' will be accepted to confirm.

  Enter a value:
```

이번에는 `-` 와 함께 삭제 예상 plan 을 실행 하고, 리소스를 삭제 할지 물어 봅니다. `yes` 를 입력 하면 리소스 삭제를 시작 합니다.

```
aws_instance.this: Destroying... [id=i-0390f0e077a519e15]
aws_instance.this: Still destroying... [id=i-0390f0e077a519e15, 10s elapsed]
aws_instance.this: Still destroying... [id=i-0390f0e077a519e15, 20s elapsed]
aws_instance.this: Still destroying... [id=i-0390f0e077a519e15, 30s elapsed]
aws_instance.this: Destruction complete after 40s

Destroy complete! Resources: 1 destroyed.
```

리소스를 삭제 했습니다.
