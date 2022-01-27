# Gitpod workspace images

## workspace-aws

Contains [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/), [ECR Docker Credential Helper](https://github.com/awslabs/amazon-ecr-credential-helper), and [kubectl](https://kubernetes.io/docs/tasks/tools/).
AWS CLI assumes the given role using a [web identity token](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc.html) passed to the workspace as an environment variable named `ID_TOKEN`.

Usage:

```
image: ghcr.io/take-home-task/workspace-aws
tasks:
  - env:
      REGION: eu-central-1
      ROLE_ARN: arn:aws:iam::123412341234:role/example
    command: |
      [ -n "$ID_TOKEN" ] && configure-awscli "$ROLE_ARN" "$REGION" && configure-ecr-login
      [ -n "$CLUSTER" ] && update-kubeconfig "$CLUSTER" "https://$CLUSTER.api.example.com"
```
