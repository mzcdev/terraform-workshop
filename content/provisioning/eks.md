---
title: EKS
weight: 36
---

EKS cluster 를 생성하고, on-demand 와 spot instance 로 구성된 Worker node 를 생성 합니다.

![EKS](../../provisioning/images/terraform_eks_ach.png)

다음 파일에서 **terraform-workshop-seoul** 을 생성한 버켓명으로 변경해줍니다.

```bash
# export BUCKET="terraform-nalbam-seoul"

cd terraform-env-workshop/eks

sed -i "s/terraform-workshop-seoul/${BUCKET}/g" *.tf
```

Terraform 명령으로 생성 합니다.

```bash
terraform init
terraform plan
terraform apply
```

다음과 같은 메세지가 출력 되면 성공 입니다.

```bash
Apply complete! Resources: x added, 0 changed, 0 destroyed.

Outputs:

config = #

# kube config
aws eks update-kubeconfig --name workshop-eks --alias workshop-eks

# or
mkdir -p ~/.kube && cp .output/kube_config.yaml ~/.kube/config

# files
cat .output/aws_auth.yaml
cat .output/kube_config.yaml

# get
kubectl get node -o wide
kubectl get all --all-namespaces

#

endpoint = https://F4CB6XXXXXXXXX53EXXXXXXXXXX5BA2.sk1.ap-northeast-2.eks.amazonaws.com
name = workshop-eks
```

kubectl 실행을 위한 권한을 획득합니다.

```bash
aws eks update-kubeconfig --name workshop-eks --alias workshop-eks
```

간단한 kubectl 명령으로 조회를 해봅니다.

```bash
kubectl get node -o wide
kubectl get all --all-namespaces
```
