# yewno

## codebuild

```shell
security add-generic-password -a GitHub -s OAUTH -w '[YOUR OAUTH TOKEN]'

pipenv run -- \
aws-vault exec testlibnd-superAdmin -- \
  aws cloudformation deploy \
    --template-file templates/codebuild.yml \
    --stack-name $(basename $(git rev-parse --show-toplevel)) \
    --parameter-overrides \
      GitHubOauth="$(security find-generic-password -w -a GitHub -l OAUTH)" \
    --capabilities CAPABILITY_NAMED_IAM
```
