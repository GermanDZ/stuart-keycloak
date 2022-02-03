# Stuart Keycloak

Dockerized local instance of [Keycloak](https://www.keycloak.org/) with JSON-based [configuration utility](https://github.com/adorsys/keycloak-config-cli).

This project is owned by :sparkles:DevEx Convoy:sparkles:. Feel free to use [#convoy-developer-experience channel](https://gostuart.slack.com/archives/C02ETTN5RGB) to reach us out.

## Setup

Prerequisites:

* [Docker](https://docs.docker.com/get-docker/) :whale:
* [Docker Compose](https://docs.docker.com/compose/install/)

If you have already `docker` and `docker-compose` installed, you can start `Keycloak` with underlaying DB by executing:
```$ docker-compose up```
To make sure that services are up, visit [Keycloak admin](`http://localhost:1080/auth`) afterwards.

## Using Keycloak Config CLI

Container with configuration tool won't run unless it's started explicitly with:
```docker-compose keycloak-config-cli```
This tool loads all the files from the `./keycloak_config` directory, applies the changes to the Keycloak and shuts itself down. Of course, the container with `Keycloak` has to be up, and there is no need to restart it to see the changes.

:warning: Instead of configuring `Keycloak` via its GUI, please use JSON files under `./keycloak_config`. They are generated with:

```
$ bin/generate_migration -h
Usage: generate_migration [migration_name]
migration_name has to be snake_cased and can't contain digits or whitespaces.

# For example:
$ bin/generate_migation snake_cased_migration_name
```

:warning: Be careful with `IMPORT_FORCE` option. It's easy to unintentionally override the data while using JSON files like migrations.

Learn more about `Keycloak Config CLI` JSON file syntax from [GitHub repository](https://github.com/adorsys/keycloak-config-cli) and check out [examples](https://github.com/adorsys/keycloak-config-cli/tree/main/src/test/resources/import-files).

## Deployment

TODO