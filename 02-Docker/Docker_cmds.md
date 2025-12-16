# Docker daily using commands

> **Note:** $indicates a normal user shell prompt.
Do not type $ while running the command.

**Note:** Depending on your Docker system configuration, you may be required to preface each `docker` command with `sudo`. 
To avoid having to use `sudo` with the `docker` command, your system administrator can create a Unix group called `docker` and add users to it.

- Note : Add the hostname in the docker group

```bash
sudo vim /etc/group
```
```md
[Adding hostname(ubuntu) in docker group]
```
<img width="733" height="347" alt="image" src="https://github.com/user-attachments/assets/09ca3478-924f-4c28-b846-915fe25dd2f7" />


**OR**
- Try this
```bash
ubuntu@ip-172-31-35-219:~$ sudo usermod -aG docker ubuntu
```
```bash
ubuntu@ip-172-31-35-219:~$ id ubuntu
```
---
**Output**
```text
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),105(lxd),113(docker)
ubuntu@ip-172-31-35-219:~$
```

## References
- [Docker hub] :(https://hub.docker.com/)
- [Docker_commands] :(https://docs.docker.com/reference/cli/docker/)

## 1 - Check the docker service are running or not
```bash
systemctl status docker
```

## 2 - List all the images

```bash
docker images
```

## 3 - Create and run a new container from an image
```bash
docker run hello-world
```

## 4 - Running container
```bash
docker ps
```

## 5 - Exited(dead) container
```bash
docker ps -a
```

## 6 - Pull the image from docker hub

## References
- [Docker Nginx] :(https://hub.docker.com/_/nginx)
```text
docker pull imagename
```

**Example:**
```bash
docker pull nginx
```

## 7 - Give the name of the image and run the background
```text
--name -> image name

-d(ditach mode)     -> run in background (continuous process not like hello-world )

Nginx runs on 80 port
```

```bash
docker run --name myweb -p 7090:80 -d nginx
```

**Additionally**
- To run the nginx website
- Turn on the EC2 intance security group Type: `All traffic`  Source: `My IP` bellow image has been shown.
  
**Edit inbound rules**

<img width="1366" height="461" alt="image" src="https://github.com/user-attachments/assets/bf4c15f8-5105-4958-b8d5-378479f2fe76" />







