# github.com/tiredofit/docker-mariadb

[![Build Status](https://img.shields.io/docker/build/tiredofit/mariadb.svg)](https://hub.docker.com/r/tiredofit/mariadb)
[![Docker Pulls](https://img.shields.io/docker/pulls/tiredofit/mariadb.svg)](https://hub.docker.com/r/tiredofit/mariadb)
[![Docker Stars](https://img.shields.io/docker/stars/tiredofit/mariadb.svg)](https://hub.docker.com/r/tiredofit/mariadb)
[![Docker 
Layers](https://images.microbadger.com/badges/image/tiredofit/mariadb.svg)](https://microbadger.com/images/tiredofit/mariadb)

# Introduction

Dockerfile to build a [MariaDB Server](https://mariadb.org) Image.
It has the same configuration variables as the Official [MySQL Image](https://github.com/docker-library/mysql)

* This Container uses a [customized Alpine Linux base](https://hub.docker.com/r/tiredofit/alpine) which includes [s6 overlay](https://github.com/just-containers/s6-overlay) enabled for PID 1 Init capabilities, [zabbix-agent](https://zabbix.org) based on `3.4` compiled for individual container monitoring, Cron also installed along with other tools (bash,curl, less, logrotate, mariadb-client, nano, vim) for easier management. It also supports sending to external SMTP servers..


[Changelog](CHANGELOG.md)

# Authors

- [Dave Conroy](https://github.com/tiredofit)

# Table of Contents

- [Introduction](#introduction)
    - [Changelog](CHANGELOG.md)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
    - [Database](#database)
    - [Data Volumes](#data-volumes)
    - [Environment Variables](#environmentvariables)   
    - [Networking](#networking)
- [Maintenance](#maintenance)
    - [Shell Access](#shell-access)
   - [References](#references)

# Prerequisites


# Installation

Automated builds of the image are available on [Docker Hub](https://hub.docker.com/r/tiredofit/mariadb) and is the recommended method of installation.


```bash
docker pull tiredofit/mariadb
```

# Quick Start

* The quickest way to get started is using [docker-compose](https://docs.docker.com/compose/). See the examples folder for a working [docker-compose.yml](/examples/docker-compose.yml) that can be modified for development or production use.

* Set various [environment variables](#environment-variables) to understand the capabilities of this image.
* Map [persistent storage](#data-volumes) for access to configuration and data files for backup.

# Configuration

### Data-Volumes

The following directories are used for configuration and can be mapped for persistent storage.

| Directory | Description |
|-----------|-------------|
| `/var/lib/mysql` | MySQL Data Directory |
| `/etc/mysql/conf.d` | Optional directory to put .cnf files for additional directives |



### Environment Variables

Along with the Environment Variables from the [Base image](https://hub.docker.com/r/tiredofit/alpine), below is the complete list of available options that can be used to customize your installation.

| Parameter | Description |
|-----------|-------------|
| `CHARACTER_SET` | Set Default Character set `utf8`, `utf8mb4` (Default `utf8mb4`)
| `MYSQL_ROOT_PASSWORD` | Root Password for Instance (e.g. password) |
| `MYSQL_DATABASE` | Optional - Automatically Create Database - Seperate with commas for multiple databases |
| `MYSQL_USER` | Optional - Automatically Assign Username Priveleges to Database (e.g. mysqluser) |
| `MYSQL_PASSWORD` | Password for authentication to above database (e.g. mysqluser) |

### Networking

The following ports are exposed.

| Port      | Description |
|-----------|-------------|
| `3306` 	   	| MariaDB Server | 		    |

# Maintenance
#### Shell Access

For debugging and maintenance purposes you may want access the containers shell. 

```bash
docker exec -it (whatever your container name is e.g. mariadb) bash
```

# References

* https://mariadb.org
