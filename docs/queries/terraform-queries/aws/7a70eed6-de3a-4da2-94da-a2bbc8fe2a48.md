---
title: IAM Password Without Symbol
hide:
  toc: true
  navigation: true
---

<style>
  .highlight .hll {
    background-color: #ff171742;
  }
  .md-content {
    max-width: 1100px;
    margin: 0 auto;
  }
</style>

-   **Query id:** 7a70eed6-de3a-4da2-94da-a2bbc8fe2a48
-   **Query name:** IAM Password Without Symbol
-   **Platform:** Terraform
-   **Severity:** <span style="color:#C60">Medium</span>
-   **Category:** Best Practices
-   **URL:** [Github](https://github.com/Checkmarx/kics/tree/master/assets/queries/terraform/aws/iam_password_without_symbol)

### Description
IAM password should have the required symbols<br>
[Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_account_password_policy)

### Code samples
#### Code samples with security vulnerabilities
```tf title="Positive test num. 1 - tf file" hl_lines="9 5"
resource "aws_iam_account_password_policy" "positive1" {
  require_lowercase_characters   = true
  require_numbers                = true
  require_uppercase_characters   = true
  require_symbols                = false
  allow_users_to_change_password = true
}

resource "aws_iam_account_password_policy" "positive2" {
  minimum_password_length        = 3
  require_lowercase_characters   = true
  require_numbers                = true
  require_uppercase_characters   = true
  allow_users_to_change_password = true
}
```


#### Code samples without security vulnerabilities
```tf title="Negative test num. 1 - tf file"
resource "aws_iam_account_password_policy" "negative1" {
  minimum_password_length        = 8
  require_lowercase_characters   = true
  require_numbers                = true
  require_uppercase_characters   = true
  require_symbols                = true
  allow_users_to_change_password = true
}

```
