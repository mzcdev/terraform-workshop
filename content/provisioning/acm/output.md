---
title: output.tf
weight: 109
---

인증서 arn 뿐 아니라, route53 의 zond_id 도 같이 리턴하여 활용 할수 있도록 했습니다.

```hcl
output "zone_id" {
  value = data.aws_route53_zone.this.id
}

output "name" {
  value = data.aws_route53_zone.this.name
}

output "certificate_id" {
  value = aws_acm_certificate.cert.id
}

output "certificate_arn" {
  value = aws_acm_certificate.cert.arn
}
```
