<!-- DO NOT EDIT THIS FILE! -->
<!-- Instead edit recipe/flow_framework.php -->
<!-- Then run bin/docgen -->

# How to Deploy Flow Framework

[Source](/recipe/flow_framework.php)

## How to deploy a Flow Framework project with zero downtime?

- First, [install](/docs/installation.md) the Deployer. 
- Second, require `recipe/flow_framework.php` recipe into your _deploy.php_ or _deploy.yaml_ file.
- Third, now you can have a zero downtime deployment!

Did you know that you can deploy **Flow Framework** project with a single command? Just execute `dep deploy`.
Something went wrong? Just run `dep rollback` to rollback your changes.
Also, you can take an advantage of the [Deployer's CLI](/docs/cli.md) to deploy your project.

Another cool feature of the Deployer is [provisioning](/docs/recipe/provision.md). Take any server, and run `dep provision` command.
This command will configure webserver, databases, php, ssl certificates, and more. 
You will get everything you need to run your **Flow Framework** application.

Deployer does next steps to [deploy](#deploy) **Flow Framework**:
* Displays info about deployment
* Prepares host for deploy
* Locks deploy
* Prepares release
* Updates code
* Creates symlinks for shared files and dirs
* Makes writable dirs
* Installs vendors
* Applies database migrations
* Publishes resources
* Creates symlink to release
* Unlocks deploy
* Cleanup old releases


The flow_framework recipe is based on the [common](/docs/recipe/common.md) recipe.

## Configuration
### flow_context
[Source](https://github.com/deployphp/deployer/blob/master/recipe/flow_framework.php#L9)

Flow-Framework application-context

```php title="Default value"
'Production'
```


### flow_command
[Source](https://github.com/deployphp/deployer/blob/master/recipe/flow_framework.php#L12)

Flow-Framework cli-command

```php title="Default value"
'flow'
```


### shared_dirs
[Source](https://github.com/deployphp/deployer/blob/master/recipe/flow_framework.php#L15)

Overrides [shared_dirs](/docs/recipe/deploy/shared.md#shared_dirs) from `recipe/deploy/shared.php`.

Flow-Framework shared directories

```php title="Default value"
[
    'Data/Persistent',
    'Data/Logs',
    'Configuration/{{flow_context}}'
]
```



## Tasks

### deploy:run_migrations
[Source](https://github.com/deployphp/deployer/blob/master/recipe/flow_framework.php#L25)

Applies database migrations.

Apply database migrations


### deploy:publish_resources
[Source](https://github.com/deployphp/deployer/blob/master/recipe/flow_framework.php#L33)

Publishes resources.

Publish resources


### deploy
[Source](https://github.com/deployphp/deployer/blob/master/recipe/flow_framework.php#L41)

Deploys your project.

Main task


This task is group task which contains next tasks:
* [deploy:prepare](/docs/recipe/common.md#deployprepare)
* [deploy:vendors](/docs/recipe/deploy/vendors.md#deployvendors)
* [deploy:run_migrations](/docs/recipe/flow_framework.md#deployrun_migrations)
* [deploy:publish_resources](/docs/recipe/flow_framework.md#deploypublish_resources)
* [deploy:publish](/docs/recipe/common.md#deploypublish)


