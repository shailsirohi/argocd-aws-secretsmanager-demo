#Update the policy statement<br>
Update policy statement to replace the correct aws region and account id. You can also change the secret path prefix as per requirement.<br>

```

# Create new policy
aws iam create-policy --policy-name argocd-awssecrets-policy --policy-document file://argocd-vault-plugin-policy.json

Copy the iam policy arn

# Create new iam user
aws iam create-user --user-name argocd-aws-secrets-user

# Create access key and secret key
aws iam create-access-key --user-name argocd-aws-secrets-user

# Attach policy to user
aws iam attach-user-policy --user-name argocd-aws-secrets-user --policy-arn <POLICY ARN FOR argocd-aws-secrets-policy>

# Create sample secret
aws secretsmanager create-secret --name sample/sec1 --secret-string "{\"secretkey\":\"MySecret\"}"

```
