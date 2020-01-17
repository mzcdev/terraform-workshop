---
title: Environment Variables
weight: 102
---

Terraform은 동작의 다양한 측면을 사용자 정의하기 위한 여러 환경 변수를 사용할 수 있습니다.

### TF_VAR_name

환경 변수를 사용하여 변수를 설정할 수 있습니다. 환경 변수는 TF_VAR_name 형식 입니다.

```
export TF_VAR_region='us-west-1'
export TF_VAR_ami='ami-049d8641'
export TF_VAR_alist='[1, 2, 3]'
export TF_VAR_amap='{ foo = "bar", baz = "qux" }'
```
