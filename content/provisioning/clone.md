---
title: Clone
weight: 31
---

환경 구성에 필요한 소스를 복제 합니다.

```bash
git clone https://github.com/mzcdev/terraform-env-workshop
```

디렉토리 구조는 다음과 같습니다.

```text
├── README.md
├── eks
│   ├── main.tf
│   ├── output.tf
│   └── variable.tf
├── instance
│   ├── main.tf
│   ├── output.tf
│   └── variable.tf
├── lambda
│   ├── lambda.zip
│   ├── main.tf
│   ├── output.tf
│   ├── src
│   │   ├── index.js
│   │   └── package.json
│   └── variable.tf
└── vpc
    ├── main.tf
    ├── output.tf
    └── variable.tf
```
