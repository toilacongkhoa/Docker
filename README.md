# Docker Learning Project

This repository contains a small Node.js application built while learning Docker.

## Command Help

Most Docker commands support `-h` to display help.

```bash
docker -h         # Show general Docker help(-h)
docker ps -h      # Show help(-h) for a specific command
```

## Build the Image

```bash
docker build .
```

## Run Containers

Replace `<image-id>` with the image ID returned by the build command.

By default, `docker run` runs in attached mode and displays the container's output in your terminal.

```bash
docker run -p 3000:80 <image-id>     # publish(-p) container port 80 on port 3000 of your machine
docker run -p 3000:80 -d <image-id>  # Run in detached(-d) mode in the background
docker run -it <image-id>           # Run the app with interactive(-i) input and a tty(-t)
```

The `-p <host-port>:<container-port>` option maps the port on your machine (left) to the port inside the container (right). With `-p 3000:80`, open http://localhost:3000 to reach the app listening on port 80 in the container.

## List Containers

```bash
docker ps     # Running containers
docker ps -a  # all(-a) containers, including stopped ones
```

## Stop the Container

Use the container name shown by `docker ps -a`.

```bash
docker stop <container-name>  # Stop a running container
```

## Start a Stopped Container

Use the container name shown by `docker ps -a`.

By default, `docker start` starts a stopped container in detached mode, without attaching your terminal.

```bash
docker start <container-name>     # Start an existing stopped container
docker start -a <container-name>  # Start the container and attach(-a) to its output
```

## Attach to a Running Container

```bash
docker attach <container-name>  # Attach your terminal to the running container's input and output streams
```

## View Container Logs

```bash
docker logs <container-name>     # Show the container's available recorded logs
docker logs -f <container-name>  # Show recorded logs and follow(-f) new output as it appears
```
