---
title: Configuration Language
weight: 310
---

Terraform은 `HCL`(Hashicorp Configuration Language) 이라는 인프라에 대한 간결한 설명이 가능하도록 설계된 자체 구성 언어를 사용합니다.

### Resources and Modules

Terraform 언어의 주요 목적은 `Resource`를 선언하는 것입니다. 리소스는 단일 인프라 개체를 정의 합니다.

리소스 그룹을 `Module`이라는 더 큰 구성 단위를 만들수 있습니다.

### Arguments, Blocks, and Expressions

```
resource "aws_vpc" "main" {
  cidr_block = var.base_cidr_block
}

<BLOCK TYPE> "<BLOCK LABEL>" "<BLOCK LABEL>" {
  # Block body
  <IDENTIFIER> = <EXPRESSION> # Argument
}
```

* `Block`은 다른 내용의 컨테이너이며 일반적으로 리소스와 같은 일종의 개체 구성을 나타냅니다. 블록은 `Block Type`을 가지며 0 개 이상의 `Block Label`을 가질 수 있으며 여러 개의 인수와 중첩 된 블록을 포함하는 본문을 갖습니다.

* `Argument`는 이름에 값을 할당합니다. 그것들은 블록 안에 작성합니다.

* `Expression`은 문자 그대로 또는 다른 값을 참조하고 결합하여 값을 나타냅니다. 인수의 값으로 또는 다른 표현식 내에 나타납니다.

### Code Organization

Terraform은 확장자가 .tf 인 파일을 사용합니다. json 기반일 경우 .tf.json 을 사용 합니다.

모듈은 하나의 디렉토리에 포함된 테라폼 파일의 모음 입니다. 루트 모듈은 테라폼이 실행될 때 현재 작업 디렉토리의 구성 파일에서 빌드되며이 모듈은 다른 디렉토리의 하위 모듈을 참조 할 수 있으며, 다른 모듈 등을 참조 할 수 있습니다.

### Configuration Ordering

일반적으로 Terraform의 블록 순서는 중요하지 않습니다. 구성의 정의 관계에 따라 리소스를 자동으로 처리합니다.

### Terraform CLI vs. Providers

`Terraform CLI`는 Terraform 구성을 평가하고 적용하기위한 엔진입니다. Terraform 언어 구문과 전체 구조를 정의하고 원격 인프라가 주어진 구성과 일치하도록 변경 순서를 조정합니다.

Terraform은 각각 일련의 리소스 유형을 정의하고 관리하는 `Provider`라는 플러그인을 사용합니다. 대부분의 Provider는 특정 클라우드 또는 온-프레미스 인프라 서비스와 연결되어 있으므로 Terraform은 해당 서비스 내에서 인프라 개체를 관리 할 수 ​​있습니다.

* https://www.terraform.io/docs/configuration/index.html
