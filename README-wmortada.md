# CiviCRM buildkit on Docker

These are additional instructions to complement the main [README](README.md) file. I have made minor customisations to Michael McAndrew's buildkit set up to enable it to work in my environment.

## Getting started

To get around the issue of a different UID (1001 rather than 1000), we need to use the `docker-compose-build.yml` file rather than `docker-compose.yml`.

* Copy the bash aliases from `bash_aliases.txt` into your bash aliases file (`~/.bash_aliases`).
* Add `startup.sh` as a run script in PhpStorm.

## Upgrading

Follow instructions in main [README](README.md).

If there have been changes to the image it can be rebuilt by running: 

`docker-compose -f docker-compose-build.yml build`

## Publishing

See instructions in main [README](README.md).

Rather than installing PHP and composer locally, this can be done using Docker images as follows:

1. `cd publish`
1. `docker run -it --rm -v "$PWD":/app composer install`
1. `docker run -it --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp php:latest php publish.php`