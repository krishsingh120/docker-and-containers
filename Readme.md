# Docker Commands Notes (Step-by-Step – As I Learned)

---

## 1️⃣ Docker Check

```bash
docker --version
docker info
```

## 2️⃣ Image Build (Basic)

```bash
docker build -t my-image .
```

## 3️⃣ Container Run (Basic)

```bash
docker run my-image
```

## 4️⃣ Run Container in Detached Mode + Port Mapping
```bash
docker run -it -d -p <host_port>:<container_port> my-image
docker run -it -d -p 3001:3000 my-image
```

## 5️⃣ Run Container with Name & Init
```bash
docker run -d --init --name <my-container> -p 3001:3000 my-image
```

## 6️⃣ List Containers
```bash
docker ps
docker ps -a
```

## 7️⃣ List Images
```bash
docker images
```

## 8️⃣ Stop / Remove Container
```bash
docker stop <container_id>
docker rm <container_id>
```

## 9️⃣ Remove Image
```bash
docker rmi <image_id>
```

## 🔟 View Logs
```bash
docker logs <container_id>
```

## 1️⃣1️⃣ Exec Inside Container and open bash
```bash
docker exec -it <container_id> sh bash
```

## 1️⃣2️⃣ Bind Mount (2-Way Sync)
```bash
docker run -it -p 3000:3000 -v "$(pwd):/developer/nodejs/app" my-image
```

## 1️⃣3️⃣ Create Volume
```bash
docker volume create my-volume
```

## 1️⃣4️⃣ List / Inspect Volumes
```bash
docker volume ls
docker volume inspect my-volume
```

## 1️⃣5️⃣ Run with Named Volume (node_modules safe)
```bash
docker run -it -p 3005:3005 -v "$(pwd):/developer/nodejs/api-gateway" -v my-volume:/developer/nodejs/api-gateway/node_modules api-gateway
```

## 1️⃣6️⃣ Create Network (Microservices)
```bash
docker network create microservice-bridge
```

## 1️⃣7️⃣ List / Inspect Networks
```bash
docker network ls
docker network inspect microservice-bridge
```

## 1️⃣8️⃣ Run Container in Custom Network
```bash
docker run -it --network microservice-bridge -p 3005:3005 api-gateway
```


## 1️⃣9️⃣ Docker Compose – Start
```bash
docker compose up --build
```

## 2️⃣0️⃣ Docker Compose – Stop
```bash
docker compose down
```

## 2️⃣1️⃣ Clean Up (Danger Zone)
```bash
docker system prune
docker volume prune
docker network prune
```
-------

## 🔹Login to Docker Hub

```bash
docker login
docker login -u <username>  ### OR (recommended – using username)
```

## 🔹 Build Docker Image
```bash
docker build -t app-setup-from-github .
```

## 🔹 Tag Image for Docker Hub
```bash
docker tag <local-image--name> <username>/<repo-name>:latest
docker tag app-setup-from-github <username>/github-app
```

## 🔹 Push Image to Docker Hub
```bash
docker push <username>/github-app:latest
```

## 🔹 Verify Local Images
```bash
docker images
```

## 🔹 Pull Image from Docker Hub (Test)
```bash
docker pull <username>/github-app:latest
```
## 🔹 Run Image from Docker Hub
```bash
docker run -d -p 3001:3000 <username>/github-app:latest
```

## 🔹 Logout from Docker Hub
```bash
docker logout
```
