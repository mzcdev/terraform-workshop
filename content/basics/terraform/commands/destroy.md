---
title: destroy
weight: 102
---

`terraform destroy` 명령은 Terraform 관리 인프라를 삭제하는 데 사용됩니다.

### Usage

```
terraform destroy [options] [dir]
```

Terraform에서 관리하는 인프라가 파괴됩니다. 파괴하기 전에 확인을 요청합니다.

이 명령은 계획 파일 인수를 제외하고 apply 명령이 수락하는 모든 인수 및 플래그를 승인합니다.

`-auto-approve`가 설정되면 삭제 확인이 표시되지 않습니다.

"종속성"에 영향을주는 대신 `-target` 플래그는 지정된 대상에 의존하는 모든 자원도 삭제합니다. 자세한 내용은 `terraform plan` 의 `target` 문서를 참조하십시오.

terraform destroy 명령의 동작은 `terraform plan -destroy` 명령으로 언제든지 미리 볼 수 있습니다.
