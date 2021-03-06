---
title: plan
weight: 110
---

`terraform plan` 명령은 실행 계획을 작성하는 데 사용됩니다. Terraform은 명시 적으로 비활성화되지 않은 경우 새로 고침을 수행 한 다음 구성 파일에 지정된 원하는 상태를 달성하는 데 필요한 작업을 결정합니다.

이 명령은 실제 자원이나 상태를 변경하지 않고 일련의 변경에 대한 실행 계획이 예상과 일치하는지 확인하는 편리한 방법입니다. 예를 들어, 버전 제어에 대한 변경 사항을 commit 하기 전에 테라 폼 계획을 실행하여 예상대로 작동 함을 확신 할 수 있습니다.

### Usage

```
terraform plan [options] [dir]
```

### Options

`-destroy` - 설정된 경우 알려진 모든 자원을 삭제하는 계획을 생성합니다.

`-input=true` - 직접 설정되지 않은 경우 변수 입력을 요청합니다.

`-target=resource` - 타겟팅 할 리소스 주소입니다. 이 플래그는 여러 번 사용할 수 있습니다. 자세한 내용은 아래를 참조하십시오.

`-var 'foo=bar'` - Terraform 구성에서 변수를 설정합니다. 이 플래그는 여러번 설정할 수 있습니다. 변수 값은 HCL로 해석되므로 이 플래그를 통해 목록 및 맵 값을 지정할 수 있습니다.

`-var-file=foo` - Terraform 구성의 변수를 변수 파일에서 설정합니다. terraform.tfvars 또는 .auto.tfvars 파일이 현재 디렉토리에 있으면 자동으로 로드됩니다. 이 플래그는 여러 번 사용할 수 있습니다.

### Resource Targeting

`-target` 옵션을 사용하면 리소스의 하위 집합에만 Terraform의 주의를 집중시킬 수 있습니다. 자원 주소 구문은 제한 조건을 지정하는 데 사용됩니다.

이 타겟팅 기능은 실수 복구 또는 Terraform 제한 문제 해결과 같은 예외적 인 상황을 위해 제공됩니다. 일상적인 작업에는 -target을 사용하지 않는 것이 좋습니다. 이로 인해 구성 드리프트가 감지되지 않고 실제 자원 상태가 구성과 어떻게 관련 되는지 혼동 될 수 있습니다.
