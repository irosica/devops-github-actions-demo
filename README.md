# CI/CD proof-of-concept.

### The main ideia of this repository is to reproduce the steps shown in [Tiago Nascimento](https://github.com/tiagonnascimento)'s [standard model](https://www.linkedin.com/pulse/setting-up-your-salesforce-repository-github-cicd-using-nascimento/) for configuring a CI/CD enabled environment in a Salesforce [Org Development Model](https://developer.salesforce.com/tools/vscode/en/user-guide/development-models), using the Github Action [sfdx-orgdev-build-deploy](https://github.com/marketplace/actions/sfdx-orgdev-build-deploy).

## Setup requirements:
* Git client
* Salesforce CLI
* Open SSL or another similar toolkit
* Visual Studio Code
* Salesforce Extension Pack Plugin for VS Code
* Salesforce CLI Integration Plugin for VS Code

## Branches Utilized
* master
* develop
* feature/**

## Org Types Utilized
* 1 Production Org (PROD)
* 1 Partial Copy Sandbox (QA01)
* 1 Developer Pro Sandbox (BUILD01)
* 1 Developer Sandbox (DEV01)

## Abstract
The environment map constructed here is regarded to enable an automated deployment pipeline based on [gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) principles. With the setup we have done here, the most important points are: 
1. Every time that a feature/** branch is developed on our DEV01 sandbox and pushed to our repository, it automatically reproduces an automated deploy on our BUILD01 sandbox, veryfing if this deploy is breaking the whole code or not, considering that we could have another developers working on different sandboxes.
2. After that, if a pull request of this feature is accepted into develop, this reproduces another automated deploy on our QA01 sandbox, enabling continuous integration between these environments. 
3. Finally, when develop is merged into master, it reproduces an automated deploy on our PROD org.

<img src="images/simple%20environment" widht="100">

## Considerations
This approach is simplified, we could make our branching strategy a little more complex, depending on the needs and size of your project. It is clear that we didn't have touched the UAT/SIT environment.

## Read All About It

- [Salesforce Extensions Documentation](https://developer.salesforce.com/tools/vscode/)
- [Salesforce CLI Setup Guide](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_intro.htm)
- [Salesforce DX Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_intro.htm)
- [Salesforce CLI Command Reference](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference.htm)
