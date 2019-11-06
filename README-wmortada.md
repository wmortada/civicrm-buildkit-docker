# CiviCRM buildkit on Docker

These are additional instructions to complement the main [README](README.md) file. I have made minor customisations to Michael McAndrew's buildkit set up to enable it to work in my environment.

## Getting started

To get around the issue of a different UID (1001 rather than 1000), we need to use the `docker-compose-build.yml` file rather than `docker-compose.yml`.

* Copy the bash aliases from `bash_aliases.txt` into your bash aliases file (`~/.bash_aliases`).
* Add `startup.sh` as a run script in PhpStorm.

## Upgrading

The docker image can be updated with the following commands:

```bash
bk down
git checkout master
git pull upstream master
docker volume rm civicrm-buildkit-docker_buildkit
bk build --no-cache
bku
```

See instructions in [README](README.md#upgrading) for details.

Buildkit can be upgraded with the following commands:

```bash
bkc git pull
bkc ./bin/civi-download-tools
```

See [documentation](https://docs.civicrm.org/dev/en/latest/tools/buildkit/#upgrading) for more details.
