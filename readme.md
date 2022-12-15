# Lyle's Reusable Azure DevOps Pipelines

This repository contains a collection of Azure Pipelines, Pipes, and Templates that I have created and used in my own projects.  I hope that you find them useful as well.

There are three main folders of resources in this repository:

- The **pipeline_examples** folder contains the example main YML files that you will want to copy to your projects and modify. Hopefully, all of the other files will be referenced and not copied to your projects.

- The **pipes** folder contains pipes that will be reused in projects that use this repo. These files should *NOT* be copied to your projects unless necessary.

- The **templates** folder contains templates that will be reused in projects that use this repo. These files should *NOT* be copied to your projects unless necessary.

---

## Pipeline Examples

The YML pipeline examples have a step in them that adds this repo as a repository in your pipeline.
It checks out this repo, then you can reference the pipes and templates in this repo.

### Check Out Example

```yaml
resources:
  repositories:
  - repository: pipelineLibrary # Internal name for this repo
    type: github
    endpoint: yourServiceConnection # Name of service connection with access to repo
    name: yourOrg/yourRepoName # Org/name of pipeline template repo
```

### Usage Example

When you want to use a template from the library, reference it with the path to the template followed by an '@' and the name of the repository you added in the checkout step.

```yaml
- template: /pipes/infra-only-pipe.yml@pipelineLibrary
```

---

## Reference

[Check out multiple repositories in your pipeline - Microsoft Learn](https://learn.microsoft.com/en-us/azure/devops/pipelines/repos/multi-repo-checkout?view=azure-devops)

[Azure DevOps multistage pipeline YAML - StackOverflow](https://stackoverflow.com/questions/61729574/azure-devops-multistage-pipeline-yaml-how-to-checkout-multiple-repos)

