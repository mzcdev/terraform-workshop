---
title: Data Sources
weight: 316
---

Data Source를 통해 Terraform 구성의 다른 곳에서 사용하기 위해 데이터를 가져 오거나 계산할 수 있습니다. 데이터 소스를 사용하면 Terraform 구성이 Terraform 외부에서 정의되거나 다른 별도의 Terraform 구성으로 정의 된 정보를 사용할 수 있습니다.

### Using Data Sources

`data` 블록을 사용 하여 설정 합니다. Terraform이 지정된 데이터 소스 `aws_ami`에서 읽고 해당 로컬 이름 `example`으로 결과를 내보내도록 요청합니다.

블록 본문 내에 ({와} 사이) 데이터 소스에 의해 정의 된 쿼리 제한 조건이 있습니다. 이 섹션의 대부분의 인수는 데이터 소스에 따라 다르며 실제로이 예에서 `most_recent`, `owners` 및 `tags`는 모두 `aws_ami` 데이터 소스에 대해 특별히 정의 된 인수입니다.

```
data "aws_ami" "example" {
  most_recent = true

  owners = ["self"]

  tags = {
    Name   = "app-server"
    Tested = "true"
  }
}
```
