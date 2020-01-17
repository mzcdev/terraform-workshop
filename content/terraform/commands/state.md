---
title: state
weight: 112
---

`terraform state` 명령은 고급 상태 관리에 사용됩니다. Terraform 사용이 향상됨에 따라 Terraform 상태를 수정해야하는 경우가 있습니다. 상태를 직접 수정하는 대신 terraform state 명령을 사용할 수 있습니다.

이 명령은 중첩 된 하위 명령이며 추가 하위 명령이 있습니다.


### Usage

```
terraform state <subcommand> [options] [args]
```

#### subcommands

* list
* mv
* pull
* push
* rm
* show

### Remote State

Terraform state 부속 명령은 모두 마치 로컬 상태 인 것처럼 원격 상태에서 작동합니다. 각 읽기 및 쓰기가 전체 네트워크 왕복을 수행하므로 읽기 및 쓰기가 평소보다 오래 걸릴 수 있습니다.
