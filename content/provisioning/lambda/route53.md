---
title: route53.tf
weight: 107
---

API Gatewat 에서 Cloud Front 를 만들었고, 이를 Route53 의 `var.domain_name` 도메인에 연결 해 줍니다.

`module.domain.certificate_arn` 를 통해 ACM 인증서를 사용 합니다.

```hcl
data "aws_route53_zone" "this" {
  name = var.domain_root
}

# https://github.com/terraform-providers/terraform-provider-aws/issues/2195
resource "aws_api_gateway_domain_name" "default" {
  domain_name     = var.domain_name
  certificate_arn = module.domain.certificate_arn
}

resource "aws_api_gateway_base_path_mapping" "default" {
  api_id      = aws_api_gateway_rest_api.default.id
  stage_name  = aws_api_gateway_deployment.default.stage_name
  domain_name = aws_api_gateway_domain_name.default.domain_name
}

resource "aws_route53_record" "default" {
  zone_id = module.domain.zone_id

  name = var.domain_name
  type = "A"

  alias {
    name                   = aws_api_gateway_domain_name.default.cloudfront_domain_name
    zone_id                = aws_api_gateway_domain_name.default.cloudfront_zone_id
    evaluate_target_health = "false"
  }
}
```
