# Example GitHub Pull Request Workflows for Snyk IaC

This is a worked example of how to use a pull request based workflow and integrate Snyk IaC checks as part of the code review process.

This uses a combination of GitHub Actions to run the `$snyk iac test` checks and GitHub Status Checks to flag the commit as success or failed.

## Example Workflow

- Developer creates a new branch e.g. `deploy-s3-bucket`
  - Makes relevant terraform changes
  - Commits branch and pushes
  - Opens a Pull Request in GitHub
- GitHub action is automatically triggered
  - `$ snyk iac test` automatically runs
  - Commit status for this SHA is set to `success` or `failed` based on the results
- Pull Request Status
  - Shows as mergeable or blocked based on the commit status

## Setup

There are some steps in order to setup this workflow

1. Setup access tokens
1. Configure your repository

### Tokens

We need to create two tokens.
Head to the settings of your repository in GitHub and click on secrets and add a new token.

_Snyk API Token_
Go to https://app.snyk.io/account and grab your API Token
Add this to GitHub Secrets called `SNYK_TOKEN`

_GitHub Token_
Go to https://github.com/settings/tokens and create a new Personal access token
Call this `GITHUB_SNYK_TOKEN` with `repo:status` permissions only.

## GitHub Actions

##
