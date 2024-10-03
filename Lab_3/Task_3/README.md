# Task_3

Create 2 nginx containers with network type bridge, enter to one of them and use curl command to view the ccontent of the other container.

### Step 1: Create a Bridge Network

First, create a custom bridge network for the containers:

```bash
docker network create my_bridge_network
```

### Step 2: Run Two Nginx Containers on the Created Network

```bash
# Run the first Nginx container
docker run -d --name nginx1 --network my_bridge_network nginx

# Run the second Nginx container
docker run -d --name nginx2 --network my_bridge_network nginx
```

### Step 3: Access One of the Containers

```bash
docker exec -it nginx1 /bin/bash
```

### Step 4: Use `curl` to Access the Other Container

```bash
curl <http://nginx2>
```

###