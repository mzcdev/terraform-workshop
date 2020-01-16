---
title: Module Composition
weight: 102
---

루트 모듈이 하나만있는 간단한 Terraform 구성에서는 간단한 리소스 집합을 만들고 Terraform의 식 구문을 사용하여 이러한 리소스 간의 관계를 설명합니다.

```hcl
resource "aws_vpc" "example" {
  cidr_block = "10.1.0.0/16"
}

resource "aws_subnet" "example" {
  vpc_id = aws_vpc.example.id

  availability_zone = "us-west-2b"
  cidr_block        = cidrsubnet(aws_vpc.example.cidr_block, 4, 1)
}
```

모듈 블록을 도입하면 구성이 단순하지 않고 계층 적이됩니다. 각 모듈에는 고유 한 리소스 세트와 자체 하위 모듈이 포함되어있어 심도 있고 복잡한 리소스 구성 트리를 만들 수 있습니다.

```hcl
module "network" {
  source = "./modules/aws-network"

  base_cidr_block = "10.0.0.0/8"
}

module "consul_cluster" {
  source = "./modules/aws-consul-cluster"

  vpc_id     = module.network.vpc_id
  subnet_ids = module.network.subnet_ids
}
```
