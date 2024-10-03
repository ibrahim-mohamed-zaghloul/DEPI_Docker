# Task_1

Create a dockerfile for ubuntu image which sleeps by default for 5 sec or sleeps according to the given number in the docker command

### Dockerfile

```docker
# Use the official Ubuntu base image
FROM ubuntu:latest

# Set default sleep duration as 5 seconds
ENV SLEEP_DURATION=5

# Set the entrypoint to sleep
ENTRYPOINT ["sleep"]

# Use the default argument for sleep duration
CMD ["${SLEEP_DURATION}"]

```

### Build and Run:

1. **Build the Docker image**:
    
    ```bash
    docker build -t ubuntu-sleeper .
    ```
    
2. **Run the container with the default 5 seconds sleep**:
    
    ```bash
    docker run ubuntu-sleeper
    ```
    
3. **Run the container with a custom sleep duration (e.g., 10 seconds)**:
    
    ```bash
    docker run ubuntu-sleeper 10
    ```