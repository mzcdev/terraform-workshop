---
title: SSH keygen
weight: 29
---

> SSH 키를 생성합니다.

```
ssh-keygen -q -f ~/.ssh/id_rsa -N "" -C "workshop"
```

> 만든 퍼블릭 키를 EC2 리전에 업로드 합니다.

```
aws ec2 import-key-pair --key-name "workshop" --public-key-material file://~/.ssh/id_rsa.pub
```
