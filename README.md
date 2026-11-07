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
docker build -t <image-name>:<tag> .  # Assign a name and tag(-t) to the image
```

If you specify an image name without a tag, Docker uses `latest`, for example `docker build -t my-app .` creates `my-app:latest`. Building without `-t` does not assign a name or tag.

## Tag an Image

```bash
docker tag <old-name>:<old-tag> <new-name>:<new-tag>  # Add a new name and tag to an existing image
```

The original name and tag remain available.

## Docker Hub Authentication

```bash
docker login   # Log in to Docker Hub
docker logout  # Log out of Docker Hub
```

## Pull an Image

```bash
docker pull <image-name>:<tag>  # Download an image from Docker Hub to your machine
```

## Run Containers

Replace `<image-id>` with the image ID returned by the build command.

By default, `docker run` runs in attached mode and displays the container's output in your terminal.

```powershell
docker run -p 3000:80 <image-id>                                      # publish(-p) container port 80 on port 3000 of your machine
docker run -d <image-id>                                              # Run in detached(-d) mode in the background
docker run -it <image-id>                                             # Accept terminal input with interactive(-i) mode and allocate a pseudo-terminal with tty(-t)
docker run --rm <image-id>                                            # Automatically remove(--rm) the container when it exits
docker run --name <container-name> <image-id>                         # Assign a name(--name) to the container
docker run -v <container-path> <image-id>                             # Create an anonymous volume(-v) at the container path
docker run -v <volume-name>:<container-path> <image-id>               # Create or reuse a named volume(-v) at the container path
docker run -v "<absolute-host-path>:<container-path>" <image-id>      # Use the volume(-v) option to bind mount a local directory into the container
```

The `-p <host-port>:<container-port>` option maps the port on your machine (left) to the port inside the container (right). With `-p 3000:80`, open http://localhost:3000 to reach the app listening on port 80 in the container.

Named volumes persist after the container is removed. `docker run --rm` removes the container and its anonymous volumes when it exits, but keeps named volumes.

For bind mounts, use an absolute host path. In PowerShell, `${PWD}` refers to the current directory.

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
docker start -a <container-name>  # Start the container and attach(-a) to display its output in your terminal
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

## Remove Stopped Containers

```bash
docker rm <container-name> [<container-name> ...]  # Remove one or more stopped containers
```

## Copy Files Between Your Machine and a Container

```bash
docker cp <local-path> <container-name>:/<destination-path>  # Copy files from your machine into the container
docker cp <container-name>:/<source-path> <local-destination-path>  # Copy files from the container to your machine
```

## List Images

```bash
docker images  # List locally available images
```

## Inspect an Image

```bash
docker image inspect <image-id>  # Show detailed information about an image
```

## Remove Images

Remove any containers using the image first, including stopped containers.

```bash
docker rmi <image-id> [<image-id> ...]  # Remove one or more images that are not used by any containers
```

## Prune Unused Images

```bash
docker image prune     # Remove dangling images that are untagged and not referenced by any container
docker image prune -a  # Remove all(-a) images not referenced by any container, including tagged images
```

Stopped containers also count as references. Docker asks for confirmation before pruning.

## List Volumes

```bash
docker volume ls  # List local volumes
```

## Remove a Volume

A volume must not be referenced by any container, including stopped containers, before it can be removed.

```bash
docker volume rm <volume-name>  # Remove a volume that is not used by any container
```

## Prune Unused Volumes

Pruning asks for confirmation and deletes data from volumes not referenced by any container, including stopped containers.

```bash
docker volume prune     # Remove unused anonymous volumes
docker volume prune -a  # Remove all(-a) unused volumes, including named volumes
```
