1. make sure there is no environment variable set up for token, key and certificates
2. commands. Get the token then sign in to the correct roles

```shell
aws configure sso --no-verify-ssl

aws sso login --profile aws-sandbox  --no-verify-ssl

aws s3 ls --profile aws-sandbox-pace  --no-verify-ssl

aws sso login --profile aws-test  --no-verify-ssl

aws sso login --profile aws-qa  --no-verify-ssl

aws sso login --profile aws-prod  --no-verify-ssl

```
3. [.config] (file:///~/.aws/config)
``` ruby
profile aws-sandbox]
sso_start_url = https://d-9a672333a0.awsapps.com/start
sso_region = us-east-2
sso_account_id = 105512447225
sso_role_name = AWS-IT-PACE-F
region = us-east-2
output = json
[profile aws-sandbox-pace]
role_arn = arn:aws:iam::105512447225:role/AWS-IM-SANDBOX-IT-PACE-Access-Role
source_profile = aws-sandbox
region = us-east-2
output = json

[profile aws-test]
sso_start_url = https://d-9a672333a0.awsapps.com/start
sso_region = us-east-2
sso_account_id = 768933643934
sso_role_name = AWS-IT-PACE-F
region = us-east-2
output = json
[profile aws-test-pace]
role_arn = arn:aws:iam::768933643934:role/AWS-IM-TEST-IT-PACE-Access-Role
source_profile = aws-test
region = us-east-2
output = json

[profile aws-qa]
sso_start_url = https://d-9a672333a0.awsapps.com/start
sso_region = us-east-2
sso_account_id = 809787276037
sso_role_name = AWS-IT-PACE-F
region = us-east-2
output = json
[profile aws-qa-pace]
role_arn = arn:aws:iam::809787276037:role/AWS-IM-QA-IT-PACE-Access-Role
source_profile = aws-qa
region = us-east-2
output = json

[profile aws-prod]
sso_start_url = https://d-9a672333a0.awsapps.com/start
sso_region = us-east-2
sso_account_id = 711275001236
sso_role_name = AWS-IT-PACE-F
region = us-east-2
output = json
[profile aws-prod-pace]
role_arn = arn:aws:iam::711275001236:role/AWS-IM-P-IT-PACE-Access-Role
source_profile = aws-prod
region = us-east-2
output = json

```

5.  How to download layers 
```bash
aws lambda get-layer-version-by-arn --arn "arn:aws:lambda:us-east-2:898466741470:layer:psycopg2-py38:1" --profile aws-sandbox-pace --no-verify-ssl

```

