---
title: Resources
weight: 312
---

Terraform 언어에서 리소스는 가장 중요한 요소입니다. 각 리소스 블록은 가상 네트워크, 컴퓨팅 인스턴스 또는 DNS 레코드와 같은 상위 구성 요소와 같은 하나 이상의 인프라 개체를 설명합니다.

### Resource Syntax

아래는 aws ec2 instance 를 생성하는 가장 심플한 코드 입니다.

```
resource "aws_instance" "sample" {
  ami           = "ami-a1b2c3d4"
  instance_type = "t2.micro"
}
```

`resource` 블록을 사용 하여 설정 합니다. `aws_instance`의 자원을 생성하며, `sample`의 이름을 가집니다.

블록 내의 `ami` `instance_type`은 aws_instance 자원 유형의 인수 입니다.

### Resource Behavior

리소스 블록은 톡정 인프라의 선언적 정의 입니다. 정의한 자원은 실제 인프라 개체를 나타내지는 않습니다.

`terraform apply` 를 통하여 설정과 구성이 일치 하도록 실제 인프라 개체를 생성, 업데이트 및 파기를 수행 합니다.

새 인프라 개체를 생성하면 `State` 에 저장되어 관리 됩니다.
