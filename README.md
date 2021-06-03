# Validation schemas for dbt configuration files

This repository contains JSON schemas that provide validation, autocomplete and documentation in VSCode for dbt configuration files:

- `dbt_project.yml`
- `packages.yml`
- `profiles.yml`
- resource configuration files located in various subfolders of dbt project
- Fivetran `deployment.yml` file

# Installation and configuration

First you need to install [YAML extension](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) for VSCode.

To enable the schemas for a single dbt project, create a file `.vscode/settings.json` in the project and add the following configuration there:

```json
{
  "yaml.schemas": {
    "https://cdn.jsdelivr.net/gh/fivetran/dbt_yaml_schemas@main/schemas/profiles.json": "profiles.yml",
    "https://cdn.jsdelivr.net/gh/fivetran/dbt_yaml_schemas@main/schemas/dbt_project.json": "dbt_project.yml",
    "https://cdn.jsdelivr.net/gh/fivetran/dbt_yaml_schemas@main/schemas/deployment.json": "deployment.yml",
    "https://cdn.jsdelivr.net/gh/fivetran/dbt_yaml_schemas@main/schemas/packages.json": "packages.yml",
    "https://cdn.jsdelivr.net/gh/fivetran/dbt_yaml_schemas@main/schemas/resources.json": [
      "models/**/*.yml",
      "analysis/**/*.yml",
      "data/**/*.yml",
      "snapshots/**/*.yml",
      "macros/**/*.yml"
    ]
  }
}
```

You may need to adjust file patterns if your project has different sctructure.

In order to enable the schemas globally, go to VSCode `Preferences` -> `Settings` -> `Extensions` -> `YAML` -> `Schemas`, click `Edit in settings.json`, paste the code above into `settings.json` and save it.

You can also specify schemas for individual files by adding the following comment to the file

```yaml
# yaml-language-server: $schema=https://cdn.jsdelivr.net/gh/fivetran/dbt_yaml_schemas@main/schemas/resources.json
```
