# Task_2

Push the images created in Problem 1&2 into your docker hub repo

### 1. Create a Docker Hub Account

If you don’t already have one, create an account on [Docker Hub](https://hub.docker.com/).

### 2. Log in to Docker Hub

Use the Docker CLI to log in to your Docker Hub account.

```bash
docker login
```

You will be prompted to enter your Docker Hub username and password.

### 3. Tag the Docker Image

```bash
docker tag ubuntu-sleeper ibrahimmohamedzaghloul/ubuntu-sleeper:latest
```

### 4. Push the Docker Image to Docker Hub

```bash
docker push ibrahimmohamedzaghloul/ubuntu-sleeper:latest
```

###