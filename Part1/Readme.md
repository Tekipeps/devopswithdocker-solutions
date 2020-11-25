### 1.1

`docker ps -a`

```bash
tekipeps@tekipeps:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS                          PORTS               NAMES
835d08b26edb        nginx               "/docker-entrypoint.…"   57 seconds ago       Up 57 seconds                   80/tcp              loving_spence
90a182605441        nginx               "/docker-entrypoint.…"   About a minute ago   Exited (0) 39 seconds ago                           unruffled_sutherland
348d025ee29c        nginx               "/docker-entrypoint.…"   2 minutes ago        Exited (0) About a minute ago                       blissful_einstein
```

### 1.2

`docker ps -a`

```bash
tekipeps@tekipeps:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

`docker images`

```bash
tekipeps@tekipeps:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```

### 1.3

> The secret message: "This is the secret message" </br>
> Steps: </br>
> Navigate to the repo in docker hub </br>
> Check the readme.md for the password </br>
> Input the password in the terminal

### 1.4

> Secret message: "Docker is easy"

#### commands:

`docker run -d devopsdockeruh/exec_bash_exercise`

```bash
tekipeps@tekipeps:~$ docker run -d devopsdockeruh/exec_bash_exercise
559c4c92a96c1e184bfb583304386bd012e7a2cf78c606bea0e377a48a154096
```

`docker exec -it 559c4c92a96c bash`

```bash
tekipeps@tekipeps:~$ docker exec -it 559c4c92a96c bash
root@559c4c92a96c:/usr/app#
```

`tail -f ./logs.txt`

```bash
root@559c4c92a96c:/usr/app# tail -f ./logs.txt
Thu, 19 Nov 2020 23:54:12 GMT
Secret message is:
"Docker is easy"
Thu, 19 Nov 2020 23:54:18 GMT
Thu, 19 Nov 2020 23:54:21 GMT
Thu, 19 Nov 2020 23:54:24 GMT
Thu, 19 Nov 2020 23:54:27 GMT
Secret message is:
"Docker is easy"
Thu, 19 Nov 2020 23:54:33 GMT
^C
root@559c4c92a96c:/usr/app#
```

### 1.5

```bash
docker run -i ubuntu:xenial sh -c 'apt-get update -y; apt-get install curl -y; echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
```

```bash
Input website:
helsinki.fi
Searching..
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
100   231  100   231    0     0    492      0 --:--:-- --:--:-- --:--:--   493
tekipeps@tekipeps:~$

```

### 1.6

`Dockerfile`

```Docker
FROM devopsdockeruh/overwrite_cmd_exercise

WORKDIR /home/tekipeps/docker1.6
CMD ["/bin/bash"]
```

command

```bash
tekipeps@tekipeps:~$ docker run -it docker-clock -c
1
2
^Ctekipeps@tekipeps:~$
```

### 1.7

`Dockerfile`

```Dockerfile
FROM ubuntu:16.04

WORKDIR /home/tekipeps/docker1.7

RUN apt-get update && apt-get install -y curl

COPY script.sh .

CMD ["bash", "script.sh"]
```

`script.sh`

```bash
echo "Input website: "; read website; echo "Searching.."; sleep 1; curl http://$website;
```

command

```bash
docker run -it curler
```

### 1.8

commands

```bash
tekipeps@tekipeps:~/devopswithdocker-solutions$ touch logs.txt
tekipeps@tekipeps:~/devopswithdocker-solutions$ docker run -v "$(pwd)/logs.txt:/usr/app/logs.txt" devopsdockeruh/first_volume_exercise
```
