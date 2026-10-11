# Docker Learning Project

This repository contains a small Node.js application built while learning Docker.

## Build the Image

```bash
docker build .
```

## Run Containers

Replace `<image-id>` with the image ID returned by the build command.

```bash
docker run -p 3000:80 <image-id>    # Machine port(-p) 3000 -> container port 80
docker run -it <image-id>           # Run the app with interactive(-i) input and a TTY(-t)
```

The `-p <host-port>:<container-port>` option maps the port on your machine (left) to the port inside the container (right). With `-p 3000:80`, open http://localhost:3000 to reach the app listening on port 80 in the container.

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
