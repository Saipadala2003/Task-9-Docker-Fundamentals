# Task 9 — Docker Fundamentals and Container Lifecycle Management

## Academic Assignment
**Course:** MSc Artificial Intelligence  
**Task:** 9 — Docker Fundamentals and Container Lifecycle Management

This repository contains the practical work completed for Task 9, covering Docker installation/verification, image and container lifecycle management, Dockerfile creation, Nginx deployment, networking, and named-volume persistence.

## Objectives
- Verify the Docker installation and Docker Engine.
- Pull and run Docker images.
- Create, build, run, inspect, stop, and remove containers.
- Create a custom Docker image with a Dockerfile.
- Run an Nginx container and access it through a mapped host port.
- Inspect Docker networks.
- Demonstrate persistent storage using a named Docker volume.

## Environment
- Docker Desktop
- Docker Engine / Linux containers
- Windows PowerShell
- Docker version used in the practical: **29.8.0**

## Custom Dockerfile

```dockerfile
FROM python:3.12-slim

WORKDIR /app

CMD ["python", "-c", "print('Task 9: Docker container is running successfully!')"]
```

Build the image:

```powershell
docker build -t task9-python-demo .
```

Run the container:

```powershell
docker run --name task9-python-container task9-python-demo
```

Expected output:

```
Task 9: Docker container is running successfully!
```

## Nginx Test

Run Nginx with port mapping:

```powershell
docker run -d --name task9-nginx -p 8080:80 nginx
```

Open:

```
http://localhost:8080
```

The Docker Nginx welcome page confirms that the container is serving HTTP traffic through the mapped host port.

## Network Inspection

Useful commands demonstrated in the task:

```powershell
docker network ls
docker network inspect bridge
```

These commands list Docker networks and show the configuration of the default bridge network.

## Named Volume Persistence

The practical also demonstrates persistent storage with a named volume:

```powershell
docker volume create task9-data

docker run --rm -v task9-data:/data alpine sh -c "echo 'Docker volume persistence test' > /data/test.txt"

docker run --rm -v task9-data:/data alpine cat /data/test.txt
```

Expected output:

```
Docker volume persistence test
```

## Evidence
The repository is intended to contain:
- Dockerfile
- Docker command log
- Screenshots of Docker Desktop and command outputs
- Nginx browser result
- Network inspection
- Volume persistence test
- Task 9 practical report (PDF)

## Repository Structure

```
Task-9-Docker-Fundamentals/
├── README.md
├── Dockerfile
├── task9_docker_command_log.txt
├── screenshots/
│   ├── docker-version-info.png
│   ├── hello-world.png
│   ├── nginx-browser.png
│   ├── network-inspection.png
│   ├── volume-persistence.png
│   ├── dockerfile-build-run.png
│   └── docker-desktop.png
└── report/
    └── Task_9_Docker_Fundamentals_Report.pdf
```

## Learning Outcomes
This task demonstrates practical understanding of:
- Docker images versus containers
- Container lifecycle commands
- Dockerfile-based image creation
- Port mapping and containerized web services
- Docker bridge networking
- Named volumes and data persistence
- Basic Docker troubleshooting and validation

## Author
**Saikumar Padala**  
MSc Artificial Intelligence
