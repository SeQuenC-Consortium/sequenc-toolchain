# Qunicorn - Unification Layer

The repository https://github.com/qunicorn/qunicorn-core contains the core components for the SeQuenC-project.

## Dockerfile

The dockerfile is used to build the container image of qunicorn core.

Buildable confirmed with:
 - [x] Windows 10
 - [x] Windows 10 - Linux Subsystem Ubuntu
 - [ ] Linux - Ubuntu 22.0
 - [ ] MacOS - Version


The Python version is 3.11 at the moment. Updating the version can lead to dependency problems, so modify with care.

Env variables are configurable such as `CONTAINER_MODE` which can be server or in a celery worker mode.
The exposed default port is set to `5005`.

## Docker-Compose

The docker compose contains

| Container   | Description |
| ----------- | ----------- |
| Qunicorn-Server      | The Qunicorn Core in server mode, which accepts user requests       |
| Qunicorn-Worker   | One general purpose Worker        |
| Redis | The standard broker for the setup with celery|
|Postgres| The database for persistent data. |

Leave out the `DB_URL` to use a SQlite database in the qunicorn-core server.

At the moment, the database need to be filled manually with the command:
```bash
docker compose exec server python -m flask create-and-load-db
``` 

## Kubernetes

The Kubernetes file can be created with the docker compose file and the tool **kompose** (https://kompose.io/)

The created kubernetes uses a local qunicorn image.
Therefore, using **minikube** (https://minikube.sigs.k8s.io/docs/) the environment need to be set in order to find the image.