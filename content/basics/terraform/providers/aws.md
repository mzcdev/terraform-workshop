---
title: AWS Provider
weight: 101
---

AWS (Amazon Web Services) 공급자는 AWS에서 지원하는 많은 리소스와 상호 작용하는 데 사용됩니다. 공급자를 사용하려면 적절한 자격 증명으로 공급자를 구성해야합니다.

아래 그림은 AWS Provider를 선언한 예시 코드입니다.

```hcl
# Configure the AWS Provider
provider "aws" {
  region = "ap-northeast-2"
}

# Create a VPC
resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}
```

### Authentication

AWS 공급자는 인증을위한 신임 정보를 제공하는 유연한 수단을 제공합니다. 다음과 같은 방법이 순서대로 지원되며 아래에 설명되어 있습니다.

* Static credentials
* Environment variables
* Shared credentials file
* EC2 Role

#### Static credentials

{{% notice info %}}
모든 Terraform 구성에 대한 자격 증명 하드 코딩은 권장되지 않으며이 파일이 공개 버전 제어 시스템에 커밋되면 비밀 유출 위험이 있습니다.
{{% /notice %}}

```hcl
provider "aws" {
  region     = "ap-northeast-2"
  access_key = "my-access-key"
  secret_key = "my-secret-key"
}
```

#### Environment variables

AWS Access Key 및 AWS Secret Key를 각각 나타내는 AWS_ACCESS_KEY_ID 및 AWS_SECRET_ACCESS_KEY 환경 변수를 통해 자격 증명을 제공 할 수 있습니다.

```hcl
provider "aws" {}
```

```
export AWS_ACCESS_KEY_ID="my-access-key"
export AWS_SECRET_ACCESS_KEY="my-secret-key"
export AWS_DEFAULT_REGION="ap-northeast-2"
terraform plan
```

#### Shared credentials file

AWS 자격 증명 파일을 사용하여 자격 증명을 지정할 수 있습니다. 기본 위치는 Linux 및 OS X에서 `$HOME/.aws/credentials` 이거나 Windows 사용자의 경우 `%USERPROFILE%\.aws\credentials` 입니다.

```hcl
provider "aws" {
  region                  = "us-west-2"
  shared_credentials_file = "/Users/tf_user/.aws/credentials"
  profile                 = "custom-profile"
}
```

### EC2 Role

IAM 역할을 사용하여 IAM 인스턴스 프로파일이있는 EC2 인스턴스에서 Terraform을 실행중인 경우 Terraform은 메타 데이터 API 엔드 포인트에 자격 증명을 요청하기 만 합니다.

### Assume role

역할 ARN이 제공되면 Terraform은 제공된 자격 증명을 사용하여이 역할을 맡습니다.

```hcl
provider "aws" {
  assume_role {
    role_arn     = "arn:aws:iam::ACCOUNT_ID:role/ROLE_NAME"
    session_name = "SESSION_NAME"
    external_id  = "EXTERNAL_ID"
  }
}
```
