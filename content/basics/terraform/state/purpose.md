---
title: Purpose of Terraform State
weight: 101
---

Terraform이 작동하려면 상태가 필수 요건입니다. 이 페이지는 Terraform 상태가 필요한 이유를 설명합니다.

### Mapping to the Real World

Terraform은 Terraform 구성을 실제 세계에 매핑하기 위해 일종의 데이터베이스가 필요합니다. 여러분의 설정에 리소스 "aws_instance" "foo"가 있는 경우 Terraform은 이 맵을 사용하여 인스턴스 i-abcd1234가 해당 리소스로 표시되어 있음을 알 수 있습니다.

AWS와 같은 일부 공급자의 경우 Terraform은 이론적으로 AWS 태그와 같은 것을 사용할 수 있습니다. 하지만 모든 리소스가 태그를 지원하는 것은 아니며 모든 클라우드 제공 업체가 태그를 지원하는 것은 아닙니다.

따라서 실제 환경의 리소스에 구성을 매핑하기 위해 Terraform은 자체 상태 구조를 사용합니다.

### Metadata

Terraform은 리소스와 원격 객체 간의 매핑과 함께 리소스 종속성과 같은 메타 데이터도 추적해야합니다.

Terraform은 일반적으로 구성을 사용하여 종속성 순서를 결정합니다. 그러나 Terraform 구성에서 리소스를 삭제할 때 Terraform은 해당 리소스를 삭제하는 방법을 알아야합니다. Terraform은 구성에 없는 자원에 대한 맵핑이 존재하며 `destroy plan` 을 볼 수 있습니다.

### Performance

기본 매핑 외에 Terraform은 상태의 모든 리소스에 대한 속성 값의 캐시를 저장합니다.

### Syncing

기본 구성에서 Terraform은 Terraform이 실행 된 현재 작업 디렉토리의 파일에 상태를 저장합니다. 팀에서 Terraform을 사용할 때는 모든 사람이 동일한 상태로 작업하여 동일한 원격 객체에 작업을 적용하는 것이 중요합니다.
