---
title: providers
weight: 109
---

`terraform provider` 명령은 현재 구성에 사용 된 제공자에 대한 정보를 출력합니다.

### Usage

```
terraform providers [config-path]
```

예시:

```
.
├── provider.aws
├── provider.terraform
└── module.eks
    ├── provider.aws (inherited)
    ├── provider.kubernetes
    ├── provider.local
    └── provider.template
```
