---
title: graph
weight: 106
---

`terraform graph` 명령은 구성 또는 실행 계획의 시각적 표현을 생성하는 데 사용됩니다. 출력은 DOT 형식이며, GraphViz에서 차트를 생성하는 데 사용할 수 있습니다.

### Usage

```
terraform graph [options] [DIR]
```

Terraform 리소스의 시각적 종속성 그래프를 출력합니다.

그래프는 DOT 형식으로 출력됩니다. 이 형식을 읽을 수 있는 일반적인 프로그램은 GraphViz 이지만 이 형식을 읽을 수 있는 웹 서비스도 있습니다.

### Generating Images

```
terraform graph | dot -Tpng > graph.png
terraform graph | dot -Tsvg > graph.svg
```

![graph](../../commands/images/graph-example.png)

![graph](../../commands/images/graph-bastion.png)
