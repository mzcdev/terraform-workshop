---
title: Resources
weight: 313
---

Terraform 언어에서 리소스는 가장 중요한 요소입니다. 각 리소스 블록은 가상 네트워크, 컴퓨팅 인스턴스 또는 DNS 레코드와 같은 상위 구성 요소와 같은 하나 이상의 인프라 개체를 설명합니다.

### Resource Syntax

아래는 aws ec2 instance 를 생성하는 가장 심플한 코드 입니다.

```hcl
resource "aws_instance" "sample" {
  ami           = var.ami_id
  instance_type = var.instance_type
}
```

`resource` 블록을 사용 하여 설정 합니다. `aws_instance`의 자원을 생성하며, `sample`의 이름을 가집니다.

블록 내의 `ami` `instance_type`은 aws_instance 자원 유형의 인수 입니다.

### Resource Behavior

리소스 블록은 톡정 인프라의 선언적 정의 입니다. 정의한 자원은 실제 인프라 개체를 나타내지는 않습니다.

`terraform apply` 를 통하여 설정과 구성이 일치 하도록 실제 인프라 개체를 생성, 업데이트 및 파기를 수행 합니다.

새 인프라 개체를 생성하면 `State` 에 저장되어 관리 됩니다.

#### Resource Dependencies

구성의 대부분의 리소스 간에는 특별한 관계가 없으며 Terraform은 관련이 없는 여러 리소스를 동시에 변경할 수 있습니다.

그러나 일부 자원은 다른 특정 자원 이후에 처리해야합니다. 때로는 리소스 작동 방식 때문일 수도 있고 리소스 구성에 다른 리소스에서 생성 된 정보 만 필요하기도 합니다.

대부분의 리소스 종속성은 자동으로 처리됩니다. Terraform은 리소스 블록 내의 표현식을 분석하여 다른 객체에 대한 참조를 찾은 다음 해당 참조를 리소스를 생성, 업데이트 또는 파괴 할 때 암시 적 순서 요구 사항으로 취급합니다. 다른 자원에 대한 행동 종속성이있는 대부분의 자원도 해당 자원의 데이터를 참조하므로 일반적으로 자원 간 종속성을 수동으로 지정할 필요는 없습니다.

그러나 일부 종속성은 구성에서 암시 적으로 인식 될 수 없습니다. 예를 들어 Terraform이 액세스 제어 정책을 관리하고 해당 정책이 있어야하는 조치를 취해야하는 경우 액세스 정책과 해당 정책이 종속 된 리소스간에 숨겨진 종속성이 있습니다. 이러한 드문 경우에 `depend_on` 메타 인수는 명시 적으로 종속성을 지정할 수 있습니다.

### Meta-Arguments

Terraform CLI는 다음과 같은 메타 인수를 정의합니다.이 인수는 모든 자원 유형과 함께 사용하여 자원의 동작을 변경할 수 있습니다.

* `count`: 개수에 따라 여러 자원 인스턴스를 작성
* `depend_on`: 숨겨진 종속성을 지정
* `for_each`: 맵 또는 문자열 세트에 따라 여러 인스턴스를 작성
* `provider`: 기본이 아닌 공급자 구성을 선택
* `lifecycle`: 라이프 사이클 사용자 정의
* `provisioner` and `connection`: 리소스 생성 후 추가 작업을 수행

#### count

4개의 EC2 instance 를 생성 합니다.

```hcl
resource "aws_instance" "server" {
  count = 4

  ami           = var.ami_id
  instance_type = var.instance_type

  tags = {
    Name = "Server ${count.index}"
  }
}
```

#### depends_on

EC2 instance 를 생성하기 전, instance_profile 를 생성 해야 한다는 것은 aws_instance 안에 정의되어 있으므로 유추가 가능 합니다. 하지만, aws_iam_role_policy 는 Terraform 이 유추해 낼 수 없으므로 선언해 주어야 합니다.

```hcl
resource "aws_iam_role" "example" {
  name               = var.name
  assume_role_policy = "..."
}

resource "aws_iam_instance_profile" "example" {
  role = aws_iam_role.example.name
}

resource "aws_iam_role_policy" "example" {
  name   = var.name
  role   = aws_iam_role.example.name
  policy = "..."
}

resource "aws_instance" "example" {
  ami           = var.ami_id
  instance_type = var.instance_type

  iam_instance_profile = aws_iam_instance_profile.example

  depends_on = [
    aws_iam_role_policy.example,
  ]
}
```

#### for_each

Autoscaling Group 에서 mixed_instances 로 정의 할 수 있는데 var.mixed_instances 배열로 n개의 값을 전달 할 수 있습니다.

```hcl
resource "aws_autoscaling_group" "worker" {
  name = var.name

  min_size = var.min
  max_size = var.max

  vpc_zone_identifier = var.subnet_ids

  mixed_instances_policy {
    launch_template {
      launch_template_specification {
        launch_template_id = aws_launch_template.worker.id
        version            = "$Latest"
      }

      override {
        instance_type = var.instance_type
      }

      dynamic "override" {
        for_each = var.mixed_instances
        content {
          instance_type = override.value
        }
      }
    }
  }
}
```

#### lifecycle

리소스의 생명주기를 정의 합니다.

```hcl
resource "aws_launch_configuration" "worker" {
  # ...

  lifecycle {
    create_before_destroy = true
  }
}
```

`aws_launch_configuration` (bool) - 현재 업데이트 할 수없는 리소스 인수를 변경해야하는 경우 Terraform은 기존 객체를 삭제 한 다음 새로 구성된 인수로 새 대체 객체를 만듭니다. .

`prevent_destroy` (bool) - 인수가 구성에 존재하는 한 자원과 관련된 인프라 개체를 파괴하는 계획을 Terraform이 오류와 함께 거부하게합니다.

`ignore_changes` (list of attribute names) - Terraform은 실제 인프라 개체의 현재 설정에서 차이를 감지하고 구성과 일치하도록 원격 개체를 업데이트를 사도합니다. 하지만 외부에서 변경된 리소스를 변경 하고 싶지 않을때 사용 될수 있습니다.
