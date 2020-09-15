# postgres-pgadmin-docker
Docker Compose setup for learning PostgreSQL

Using this repo, you can setup PostgreSQL learning environment right away without installing PostgreSQL and pgAdmin locally.

## Features

* Postgres 12 and pgAdmin4 installed out of the box

## Requirements
* A computer that Docker and Docker Compose are installed
* Basic knowledge of Docker

## How to use
1. Run the following command in the repo's directory:
```
$ docker-compose up
```
It may take for a while when you run that command for the first time.

2. Access to http://localhost
3. Login with the user below:
```
User: admin@example.com
Password: password
```
You will be asked for the DB password, so type `password` literally and click "OK".

4. When you are done, run this command in repo's directory to shut the DB and pgAdmin server down.
```
docker-compose down
```

The DB and pgAdmin data will be preserved in the dedicated Docker volumes, so they will be still there when you run `docker-compose up` next time.

## Connecting databases using psql command-line tool

You can also connect to your DBs using psql command-line tool by the command below:

```
docker container exec -it postgres-pgadmin-docker_db_1 psql -d <DBName> -U postgres
```

## Notice

* Because pgAdmin4 runs on the server (i.e. Docker container) rather than your desktop, when you try to select local file(s) on pgAdmin4, you must upload it first.
In case of the files which are too large to upload, you can copy such files to the Docker volume instead like this:

```
docker cp AdventureWorks.tar postgres-pgadmin-docker_pgadmin_1:/var/lib/pgadmin/storage/admin_example.com
```

* If you plan to deploy this repo to the host that publically available, I strongly recommend to change default password to the strong one ASAP.

## License

This repo is licensed under the terms of [MIT license](https://github.com/cypress-io/cypress/blob/develop/LICENSE.md).
