# aws-workflows

GitHub Actions reusable workflows for working with AWS.

## Reusable workflows

### develop-ecr

Development Build - Push to ECR

This workflow should facilitate rapid development of a Dockerised application.

It should be used whilst undertaking rapid development, before a formal release is approved.

The following steps are performed by this workflow:

* Checkout

* Setup Docker BuildX

* Configure AWS SSO Credentials

* Log into ECR

* Set build tag (<CURRENT_TAG>-<GITHUB_RUN_ID>)

* Build & push Docker image to ECR

```yaml
jobs:
  build:
    uses: ripjar/aws-workflows/.github/workflows/develop-ecr.yaml@master
    with:
      aws-region: eu-west-2
      aws-iam-role: arn:aws:iam::<AWS_ACCOUNT_ID>:role/github-<GIT_REPO>-dev
      bump-version: false (default - optional)
      docker-image: <APP_NAME>
      dockerfile: ./Dockerfile (optional)
      platforms: linux/arm64,linux/amd64 (optional)
```
