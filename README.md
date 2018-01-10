# Etherpad Lite

Dockerfile inspired by [tvelocity/etherpad-lite]( https://github.com/tvelocity/dockerfiles/tree/master/etherpad-lite)

## Etherpad Lite source code

Source code come from the following [GitHub project](https://github.com/ether/etherpad-lite).

## Quickstart

> From [tvelocity/etherpad-lite]( https://github.com/tvelocity/dockerfiles/tree/master/etherpad-lite) Documentation

First you need a running mysql container, for example:

```bash
$ docker network create ep_network
$ docker run -d --network ep_network -e MYSQL_ROOT_PASSWORD=password --name ep_mysql mysql
```

Finally you can start an instance of Etherpad Lite:

```bash
$ docker run -d \
    --network ep_network \
    -e ETHERPAD_DB_HOST=ep_mysql \
    -e ETHERPAD_DB_PASSWORD=password \
    -p 9001:9001 \
    tvelocity/etherpad-lite
```

Etherpad will automatically create an `etherpad` database in the specified mysql
server if it does not already exist.
You can now access Etherpad Lite from http://localhost:9001/

## Environment variables

> From [tvelocity/etherpad-lite]( https://github.com/tvelocity/dockerfiles/tree/master/etherpad-lite) Documentation

This image supports the following environment variables:

* `ETHERPAD_TITLE`: Title of the Etherpad Lite instance. Defaults to "Etherpad".
* `ETHERPAD_PORT`: Port of the Etherpad Lite instance. Defaults to 9001.
* `ETHERPAD_SESSION_KEY`: Session key for the Etherpad Lite configuraition. You
can set this in case of migrating from another installation. A value is
automatically generated by default.

* `ETHERPAD_ADMIN_PASSWORD`: If set, an admin account is enabled for Etherpad,
and the /admin/ interface is accessible via it.
* `ETHERPAD_ADMIN_USER`: If the admin password is set, this defaults to "admin".
Otherwise the user can set it to another username.

* `ETHERPAD_DB_HOST`: Hostname of the mysql databse to use. Defaults to `mysql`
* `ETHERPAD_DB_USER`: By default Etherpad Lite will attempt to connect as root
to the mysql container.
* `ETHERPAD_DB_PASSWORD`: MySQL password to use, mandatory. If legacy links
are used and ETHERPAD_DB_USER is root, then `MYSQL_ENV_MYSQL_ROOT_PASSWORD` is
automatically used.
* `ETHERPAD_DB_NAME`: The mysql database to use. Defaults to *etherpad*. If the
database is not available, it will be created when the container is launched.

## 
