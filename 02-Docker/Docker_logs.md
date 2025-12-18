# Docker container logs

## Reference

- [Docker container logs] : (https://docs.docker.com/reference/cli/docker/container/logs/)

## Information:

**Configure logging drivers**

## Reference
- [Docker container logs] : (https://docs.docker.com/engine/logging/configure/)

Docker includes multiple logging mechanisms to help you get information from running containers and services. 
These mechanisms are called logging drivers. Each Docker daemon has a default logging driver, 
which each container uses unless you configure it to use a different logging driver, or log driver for short.

## 1 - Logs of container
```md
docker logs "container name or ID"
```

## 2 - Metadata of image (json formate)
```md
docker inspect "image name or ID"
```
**Note:**

- Cmd and Entrypoint, when we run cmd `docker run`
- It's going to run `Entrypoint` then `Cmd`.

```text
"Entrypoint": [
                "/docker-entrypoint.sh"

"Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],

```

<img width="846" height="567" alt="image" src="https://github.com/user-attachments/assets/fae7c58a-281f-4642-ab56-d3541334c465" />

**Note**
- Most of the cmds return o/p, we don't see that.
- So we run it detach mode (background).

```md
docker run -d -P "container name or ID"
```

- `docker run`: Creates and starts a new container from an image.
- `-d` (detached mode): Runs the container in the background.
- `-P` (capital P): Automatically publishes ports
- **Note:** -P vs -p (very important)
- `-p` 32768:80 : Manual port mapping
- `-P` : Automatic random port mapping

<img width="747" height="143" alt="image" src="https://github.com/user-attachments/assets/2a9fd7b0-5133-4594-8848-bed49ca79d73" />








