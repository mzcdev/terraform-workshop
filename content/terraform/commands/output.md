---
title: output
weight: 107
---

`terraform output` 명령은 상태 파일에서 출력 변수의 값을 추출하는 데 사용됩니다.

### Usage

```
terraform output [options] [NAME]
```

### Options

`-json` - 지정된 경우 출력은 출력 당 키를 사용하여 JSON 오브젝트로 형식화됩니다. NAME을 지정하면 지정된 출력 만 반환됩니다. 추가 처리를 위해 jq와 같은 도구에 파이프로 연결할 수 있습니다.
