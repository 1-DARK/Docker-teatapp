
````markdown
# 🐳 Docker Testapp

A beginner-friendly guide to understanding and using Docker efficiently — with practical commands, real-world usage, and examples.

---

## 📦 What is Docker?

Docker lets you package your app and its environment into containers so it works the same everywhere.

---


---

## 🔧 Basic Docker Commands

```bash
# Run an image
docker run -it ubuntu

# Pull an image
docker pull mysql:8.0

# View images and containers
docker images
docker ps -a

# Start / Stop / Remove
docker start <container>
docker stop <container>
docker rm <container>
docker rmi <image>
````

---

## 🌐 Port Binding

Expose container ports to the host:

```bash
docker run -p 8080:3306 mysql:8.0
```

> Host port\:container port

---

## 📁 Docker Volumes

Used to persist data outside containers.

```bash
# Bind mount
docker run -v /host/dir:/container/dir ubuntu

# Named volume
docker volume create myvol
docker run -v myvol:/data ubuntu

# View & prune
docker volume ls
docker volume prune
```

---

## 🖧 Docker Networking

Let containers talk to each other:

```bash
docker network create my-network
```



---

## 🧱 Docker Compose

Define multi-container apps in `compose.yaml`:

```yaml
version: "3.8"
services:
  mongo:
    image: mongo
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: 
      MONGO_INITDB_ROOT_PASSWORD: 

  mongo-express:
    image: mongo-express
    ports:
      - "8081:8081"
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: 
      ME_CONFIG_MONGODB_ADMINPASSWORD: 
      ME_CONFIG_MONGODB_URL: mongodb://:@mongo:27017/
    depends_on:
      - mongo
```

```bash
docker compose -f compose.yaml up -d
docker compose -f compose.yaml down
```

---

## 🐳 Dockerfile Example

```dockerfile
FROM node
ENV MONGO_DB_USERNAME= \
    MONGO_DB_PASSWORD=
RUN mkdir -p docker-testapp
COPY . /docker-testapp
CMD ["node", "/docker-testapp/server.js"]
```

---

## ⬆️ Publish Your Image

```bash
docker build -t username/appname .
docker login
docker push username/appname
```

---

## ✅ Troubleshooting

```bash
docker logs <container>
docker exec -it <container> /bin/bash
```

---

## 📚 Resources

* [Docker Docs](https://docs.docker.com/)
* [Docker Hub](https://hub.docker.com/)

```

---

Let me know if you'd like this saved as a `.md` file or need a version customized for your course or GitHub repo.
```
