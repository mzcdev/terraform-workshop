---
title: Provisioners
weight: 350
---

Provisioner를 사용하면 서버 또는 기타 인프라 개체를 서비스 할 수 있도록 로컬 컴퓨터 또는 원격 컴퓨터에서 특정 작업을 모델링 할 수 있습니다.

### Provisioners are a Last Resort

Terraform에는 Terraform의 선언적 모델에서 직접 표현할 수없는 특정 행동이 항상있을 것임을 알고 프로비저닝의 개념을 실용주의의 척도로 포함합니다.

하지만 이것은 Terraform 사용에 상당한 복잡성과 불확실성을 추가합니다. 최대한 Terraform에서 제공되는 기본 기능으로 시도하고, 다른 옵션이 없을 경우에만 Provisioner를 사용하는 것이 좋습니다.

{{% children %}}
