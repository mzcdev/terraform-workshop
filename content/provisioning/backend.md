---
title: Backend
weight: 32
---

Terraform state 정보를 저장할 S3 Bucket 를 생성 합니다.

```bash
export REGION="ap-northeast-2"
export BUCKET="terraform-workshop-seoul"
```

```bash
aws s3 mb s3://${BUCKET} --region ${REGION}
```

중복 실행을 막기 위해, DynamoDB Table 을 생성 합니다.

```bash
aws dynamodb create-table \
    --table-name ${BUCKET} \
    --attribute-definitions AttributeName=LockID,AttributeType=S \
    --key-schema AttributeName=LockID,KeyType=HASH \
    --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1 \
    --region ${REGION}
```

{{% notice tip %}}
S3 Bucket 이름으로 사용되는 **terraform-workshop-seoul** 은 다른 사용자와 중복될수 있습니다.
본인의 닉네임 등을 사용하여 유니크한 이름을 부여하도록 합니다.
{{% /notice %}}
