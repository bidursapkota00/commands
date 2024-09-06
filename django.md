## Django with Docker

### Create a new Django project

```bash
docker-compose run --rm app sh -c "django-admin startproject app ."
```

- **Description:** Runs the Django `startproject` command inside the `app` service container, initializing a new Django project.

### Run unit test in Django

```bash
docker-compose run --rm app sh -c "python manage.py test"
```

- **Description:** Runs unit test.

### Create a new Django app

```bash
docker-compose run --rm app sh -c "python manage.py startapp app_name"
```

- **Description:** Creates a new app in django project