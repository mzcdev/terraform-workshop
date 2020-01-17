---
title: providers
weight: 111
---

`terraform provider` 명령은 현재 구성에 사용 된 제공자에 대한 정보를 출력합니다.

### Usage

```
terraform providers [config-path]
```

### Example

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

```
.
├── provider.aws
├── provider.terraform
└── module.worker
    ├── provider.aws (inherited)
    └── module.worker
        └── provider.aws (inherited)
```
