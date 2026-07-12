# Docker Desktop Installation & Troubleshooting (Windows)

## Goal

Install Docker Desktop on Windows and run Linux containers using WSL 2.

## Environment

-   Windows 10 (Build 19045.6466)
-   Docker Desktop 29.6.1
-   WSL 2
-   Ubuntu 24.04

## Issues Encountered

### 1. Docker command failed

``` cmd
docker ps
```

Error:

    Error response from daemon: Docker Desktop is unable to start

### 2. WSL kernel missing

``` cmd
wsl --status
```

Reported:

    The WSL 2 kernel file is not found.

### 3. Fix WSL

Run:

``` cmd
wsl --update
wsl --shutdown
```

Restart the PC.

### 4. Verify WSL

``` cmd
wsl --version
```

Verified: - WSL version 2.7.10.0 - Kernel 6.18.33.2

Open Ubuntu:

``` cmd
wsl
```

Ubuntu started successfully.

### 5. Docker client installed

``` cmd
docker version
```

Client information displayed, but daemon connection failed.

### 6. Docker Desktop Service

Checked:

``` cmd
sc query com.docker.service
```

Service existed but was stopped.

Started it manually:

``` cmd
net start com.docker.service
```

Output:

    The Docker Desktop Service service was started successfully.

### 7. Start Docker Desktop

Opened Docker Desktop and waited for the engine to start.

### 8. Verification

``` cmd
docker ps
```

Output:

    CONTAINER ID   IMAGE   COMMAND   CREATED   STATUS   PORTS   NAMES

This confirms Docker Engine is working.

## Useful Commands

``` cmd
docker version
docker info
docker ps
docker images
docker run hello-world
docker run -d --name my-nginx -p 8080:80 nginx
docker stop my-nginx
docker start my-nginx
docker rm my-nginx
```

## Lessons Learned

-   Docker Desktop requires WSL 2 for Linux containers.
-   Ensure WSL kernel is installed and updated.
-   Verify Docker Desktop Service is running.
-   `docker ps` returning an empty list means Docker is working but no
    containers are running.

## Next Learning Plan

1.  Docker Images
2.  Docker Containers
3.  Docker Volumes
4.  Docker Networks
5.  Docker Compose
6.  Prometheus
7.  Grafana
8.  cAdvisor
9.  Traefik
10. Beszel
