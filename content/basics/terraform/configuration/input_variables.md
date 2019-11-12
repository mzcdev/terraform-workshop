---
title: Input Variables
weight: 313
---

Input Variable은 Terraform 모듈의 매개 변수 역할을하며 모듈 자체 소스 코드를 변경하지 않고 모듈의 측면을 사용자 정의 할 수 있고 다른 구성간에 모듈을 공유 할 수 있습니다.

### Declaring an Input Variable

`variable` 블록을 사용 하여 설정 합니다.

```
variable "ami_id" {
  description = "The id of the machine image (AMI) to use for the server."
  type = string
}

variable "availability_zone_names" {
  type    = list(string)
  default = ["us-west-1a"]
}

variable "docker_ports" {
  type = list(object({
    internal = number
    external = number
    protocol = string
  }))
  default = [
    {
      internal = 8300
      external = 8300
      protocol = "tcp"
    }
  ]
}
```

변수 블록의 `type` 인수를 사용하면 변수 값으로 허용되는 값 유형을 제한 할 수 있습니다. 유형 제한 조건이 설정되지 않은 경우 모든 유형의 값이 승인됩니다.

### Using Input Variable Values

변수를 선언 한 모듈 내에서 표현식 내에서 `var.<NAME>`으로 값에 액세스 할 수 있습니다.

```
resource "aws_instance" "example" {
  instance_type = "t2.micro"
  ami           = var.ami_id
}
```
