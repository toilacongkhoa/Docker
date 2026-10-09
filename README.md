# Docker Learning Project

This repository contains a small Node.js application built while learning Docker.

## Build the Image

```bash
docker build .
```

## Run the Container

Replace `<image-id>` with the image ID returned by the build command.

```bash
docker run -p 3000:3000 <image-id>
```

The `-p 3000:3000` option maps port 3000 in the container to port 3000 on your machine. Open http://localhost:3000 to view the application.

## List Running Containers

```bash
docker ps
```

## Stop the Container

Replace `<container-name>` with the container name shown by `docker ps`.

```bash
docker stop <container-name>
```
