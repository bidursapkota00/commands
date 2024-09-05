# Command Reference

This document provides a list of useful commands for **PowerShell**, **FFmpeg**, **Docker**, and **Flake8** along with descriptions for each.

---

## PowerShell

### Remove `.git` directory recursively

```powershell
Remove-Item -Path .git -Recurse -Force
```

- **Description:** Deletes the `.git` directory and all its contents recursively.

### Get a list of all files (including hidden ones)

```powershell
Get-ChildItem -Force
```

- **Description:** Lists all items in the current directory, including hidden files.

---

## FFmpeg

### Resize an image to a specific width

```bash
ffmpeg -i input.jpg -vf "scale=WIDTH:-1" output.jpg
```

- **Description:** Resizes the input image to a specified width while maintaining the aspect ratio. Replace `WIDTH` with your desired value (e.g., 800).

### Stack two images vertically

```bash
ffmpeg -i image1.jpg -i image2.jpg -filter_complex "vstack=inputs=2" merged.jpg
```

- **Description:** Vertically stacks two images (`image1.jpg` and `image2.jpg`) and outputs the result to `merged.jpg`.

### Compress an image

```bash
ffmpeg -i merged.jpg -q:v 20 output.jpg
```

- **Description:** Compresses the input image (`merged.jpg`) with a quality factor of 20 and saves the result to `output.jpg`. Lower values indicate higher quality.

### Convert PNG to JPG

```bash
ffmpeg -i input.png output.jpg
```

- **Description:** Converts a PNG image (`input.png`) to a JPG format (`output.jpg`).

---

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

---

## Flake8

### Check for linting errors using Flake8

```bash
docker-compose run --rm app sh -c "flake8"
```

- **Description:** Runs Flake8 within the `app` service container to check for Python code style and linting errors.

---
