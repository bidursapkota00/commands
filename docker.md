## Docker

### Build a Docker image

```bash
docker build .
```

- **Description:** Builds a Docker image from the Dockerfile located in the current directory.

### Build Docker services with `docker-compose`

```bash
docker-compose build
```

- **Description:** Builds Docker images for services defined in the `docker-compose.yml` configuration file.

### Create a new Django project

```bash
docker-compose run --rm app sh -c "django-admin startproject app ."
```

- **Description:** Runs the Django `startproject` command inside the `app` service container, initializing a new Django project.

### Run services

```bash
docker-compose up
```

- **Description:** Starts all services defined in the `docker-compose.yml` file, making the web application accessible locally.

### Stop and remove containers

```bash
docker compose down
```

- **Description:** The `docker compose down` command is used to stop and remove containers, networks, & optionally volumes, and images that were created by docker-compose up.

### List volumes

```bash
docker volume ls
```

- **Description:** Lists all volumes

### Remove volume

```bash
docker volume rm volume_name
```

- **Description:** Removes the volume
