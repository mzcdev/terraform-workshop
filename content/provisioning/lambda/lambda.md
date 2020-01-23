---
title: Lambda API
weight: 100
---

다음 파일에서 **terraform-workshop-seoul** 을 생성한 버켓명으로 변경해줍니다.

```bash
# export BUCKET="terraform-nalbam-seoul"

cd terraform-env-workshop/lambda

sed -i "s/terraform-workshop-seoul/${BUCKET}/g" *.tf
```

Terraform 명령으로 생성 합니다.

```bash
terraform init
terraform plan
terraform apply
```

다음과 같은 메세지가 출력 되면 성공 입니다.

```text
Apply complete! Resources: x added, 0 changed, 0 destroyed.

Outputs:

invoke_url = https://8zgxxav8oi.execute-api.ap-northeast-2.amazonaws.com/dev
```

lambda api 가 동작 하는지 테스트 해봅시다.

```bash
invoke_url="https://8zgxxav8oi.execute-api.ap-northeast-2.amazonaws.com/dev"

curl -sL -X POST -d "{\"data\":\"ok\"}" ${invoke_url}/demo | jq .
```

`ok` 가 출력 되면 성공 입니다.

```json
{
  "data": "ok"
}
```
