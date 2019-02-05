# Serverless Check Git Branch Before Deploy

Serverless framework pluging to check that current git branch is allowed to deploy to serverless stage.

## Getting Started

Add this plugin to your Serverless project following the Install directions below.

Once installed when you run `sls deploy --stage STAGE` The `STAGE` will be checked against you config to verify you are on the correct git branch to deploy that stage.

### Prerequisites

This plugin required both [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and the [Serverless Framework](https://serverless.com/framework/docs/providers/aws/guide/installation/)

### Installing

Create a folder called `.serverless_plugins` in the root of your project.

Copy the file `check-git-branch-before-deploy.js` into that folder.

Update your `serverless.yml` file with the following:

Add to custom configuration:

```yaml
custom:
    checkGitBranchBeforeDeploy:
        staging: staging
        production: production
```

Update stage to use variable

```yaml
provider:
    stage: ${opt:stage}
```

Add to plugins list

```yaml
plugins:
- check-git-branch-before-deploy
```

That's it. You've now protected yourself from deploying dev code to the production stage... maybe. :-)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to Antoine Toubhans and his [blog post](https://blog.sicara.com/control-deployment-git-aws-serverless-plugin-cd12de13abb6)
