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

## 3 - Output of the cmd executed be the container
```md
docker logs "container name or ID"
```
<img width="507" height="202" alt="image" src="https://github.com/user-attachments/assets/f2d8fdfc-8fb4-4399-b5fc-eea20645a06c" />

## 4 - Don't run in the background (attach mode)
```md
dcker run -P "container name or ID"
```
**Note:**
- Prompt back Ctrl+c

## 5 - Some container not start, It can be exited state
- See this scenario
- I have run

```md
docker run -d -P "Image name"
```
- Example: docker run -d -P mysql:5.7
- -d → Detached mode
- -P → Publish all exposed ports

<img width="433" height="92" alt="image" src="https://github.com/user-attachments/assets/f7359a8e-a564-4017-8844-a9a5c700aa62" />

- Check `docker logs`

```md
docker logs "container name or ID"
```
- It shows error in Entrypoint.

<img width="569" height="144" alt="image" src="https://github.com/user-attachments/assets/3fe355e8-c422-4ff8-81a2-94b5a9903334" />

- You need to specify the variables as shown in the above image.
- So we export the variable.
- To set password: `mypass`

```md
docker run -d -P -e MYSQL_ROOT_PASSWORD=mypass mysql:5.7
```

- -d → Detached mode
- -d → Detached mode
- -e MYSQL_ROOT_PASSWORD=mypass
  
**Note**

- Sets MySQL root user password.
- Mandatory for MySQL container to start.
- Without this:
- MySQL initialization fails, container exits.
- What happens internally (important).
- Container starts.
- MySQL entrypoint script reads environment variables.
- Root password is set to mypass.
- MySQL server starts and listens on port 3306.
- Container stays running.

<img width="654" height="88" alt="image" src="https://github.com/user-attachments/assets/cc44d331-c66f-4ee3-9586-77b9cd5ab973" />

- How to connect to this MySQL container
- Find mapped port `docker ps`
- Alternative (NO MySQL client needed on host). You can connect from inside the container

```bash
docker exec -it "container name or ID" mysql -u root -p
```

- password = mypass
- No client install,Fast,Very useful for debugging.
- Note: Why two ports are shown in docker ps

<img width="1316" height="278" alt="image" src="https://github.com/user-attachments/assets/76020acd-70ab-408a-9700-31d9ed843c31" />



```bash
32770 -> 3306  (MySQL main port)
32771 -> 33060 (MySQL X Plugin)
```

- You should use 3306 mapping only for normal MySQL connections.
- MySQL container is running
- Error was on host side, not Docker
- nstall mysql-client OR use docker exec
- Use correct -h and -P

<img width="1316" height="535" alt="image" src="https://github.com/user-attachments/assets/fba48955-205b-45c7-ae50-5c43b3ee969c" />

- Then run the command.

```md
docker inspect "container name or ID"
```

<img width="1314" height="527" alt="image" src="https://github.com/user-attachments/assets/39e676f5-47f0-4983-a657-5ef7693d45d2" />

- See the Entrypoint and CMD.

<img width="1311" height="569" alt="image" src="https://github.com/user-attachments/assets/d141517a-b130-42e7-9e31-57c020b15558" />

---
# Consistency is the key





















