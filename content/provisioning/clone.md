---
title: Clone
weight: 32
---

> 환경 구성에 필요한 소스를 복제 합니다.

```
git clone https://github.com/mzcdev/terraform-env-workshop
```

> 다음 파일에서 **terraform-workshop-seoul** 을 생성한 버켓명으로 변경해줍니다.

```
# export BUCKET="terraform-nalbam-seoul"

cd terraform-env-workshop

sed -i "s/terraform-workshop-seoul/${BUCKET}/g" ./vpc/main.tf
sed -i "s/terraform-workshop-seoul/${BUCKET}/g" ./lambda/main.tf
sed -i "s/terraform-workshop-seoul/${BUCKET}/g" ./lambda/variable.tf
```
