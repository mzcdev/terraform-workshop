---
title: Instance
weight: 32
---

가장 심플한 코드로 EC2 instance 를 만들어 보겠습니다.

#### init

Terraform 명령으로 초기화 합니다.

```bash
cd terraform-env-workshop/instance

terraform init
```

```text
Initializing the backend...

Initializing provider plugins...
- Checking for available provider plugins...
- Downloading plugin for provider "aws" (hashicorp/aws) 2.35.0...

...

* provider.aws: version = "~> 2.35"

Terraform has been successfully initialized!

...
```

aws provider 를 위한 plugin 을 다운로드 했습니다.

#### plan

Terraform 명령으로 실행 계획을 확인 합니다.

```bash
cd terraform-env-workshop/instance

terraform plan
```

```text
Refreshing Terraform state in-memory prior to plan...

------------------------------------------------------------------------

Terraform will perform the following actions:

  # aws_instance.this will be created
  + resource "aws_instance" "this" {
      ...
    }

Plan: 1 to add, 0 to change, 0 to destroy.

...
```

`+` 가 나오며 1개의 리소스를 `in-memory` 에 만들것 이라는것을 알 수 있습니다.

#### apply

Terraform 명령으로 실행 합니다.

```bash
cd terraform-env-workshop/instance

terraform apply
```

```text
Plan: 1 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value:
```

plan 을 다시한번 해보고 액션을 수행 할지 물어 봅니다. `yes` 를 입력 하면 리소스 생성을 시작 합니다.

```text
aws_instance.this: Creating...
aws_instance.this: Still creating... [10s elapsed]
aws_instance.this: Still creating... [20s elapsed]
aws_instance.this: Creation complete after 22s [id=i-0390f0e077a519e15]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

Outputs:

id = i-0390f0e077a519e15
private_ip = 172.31.39.210
```

리소스가 생성 되었습니다.
