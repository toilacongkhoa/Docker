# Docker Learning Project

This repository contains a small Node.js application built while learning Docker.

## Build the Image

```bash
docker build .
```

## Run Containers

Replace `<image-id>` with the image ID returned by the build command.

```bash
docker run -p 3000:3000 <image-id>  # Map port(-p) 3000 to your machine
docker run -it <image-id>          # Run the app with interactive(-i) input and a TTY(-t)
```

Open http://localhost:3000 after running the app with `-p 3000:3000`.

## List Containers

```bash
docker ps     # Running containers
docker ps -a  # All(-a) containers, including stopped ones
```

## Stop the Container

Replace `<container-name>` with the container name shown by `docker ps`.

```bash
docker stop <container-name>
```
