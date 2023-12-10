<div align="center">
  📦
</div>
<h1 align="center">
  set-github-variable
</h1>

<p align="center">
   A GitHub Action for updating Github Variables
</p>

<br />

### Usage

Update [Github Variable](https://docs.github.com/en/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository) for a repository or organization.

```YAML
- uses: mmoyaferrer/set-github-variable@v1.0.0
  with:
      name: 'SAMPLE_VAR'
      value: 'Hello World'
      repository: mmoyaferrer/set-github-variable
      token: ${{ secrets.REPO_ACCESS_TOKEN }}
```

### Pre-requisites

1. Create a [Github Variable](https://docs.github.com/en/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository) for your repo/organization.
2. Create an access token with access to manage actions repository variables.

### Customizing

#### inputs

The following are required

| Name         | Type   | Description                                                                                                     |
| ------------ | ------ | --------------------------------------------------------------------------------------------------------------- |
| `name`       | String | Variable name                                                                                                   |
| `value`      | String | Variable value                                                                                                  |
| `repository` | String | Repository name, with format `<organization>/<repository>` i.e `mmoyaferrer/set-github-variable`                |
| `token`      | String | [Repository Token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token) |

The following are optional, to be provided when the value is Org scoped instead of a repository variable:

| Name                    | Type            | Description                                                                                                                                                                            |
| ----------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `org`                   | Boolean         | Details if the variable belongs to an [organization](https://docs.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-organizations) (default is `false`)       |
| `visibility`            | String          | Configures access to the repositorys in the org, see [more](https://docs.github.com/en/rest/actions/variables?apiVersion=2022-11-28#update-an-organization-variable)                   |
| `selectedRepositoryIds` | String[Integer] | Array of repositories ids where to update the org-scoped variable, see [more](https://docs.github.com/en/rest/actions/variables?apiVersion=2022-11-28#update-an-organization-variable) |

#### outputs

The following outputs can be accessed via `${{ steps.<step-id>.outputs }}` from this action

| Name     | Type    | Description                   |
| -------- | ------- | ----------------------------- |
| `data`   | String  | Response data from Github API |
| `status` | Integer | Response code from Github API |
