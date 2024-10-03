# Task_2

Problem 2:  

- Create a dockerfile for nginx image with different html content and different nginx conf that listen to port 8080 instead of port 80 on the container
- Create container from the new image

### Custom Nginx Configuration (`nginx.conf`):

This file configures Nginx to listen on port 8080 instead of 80.

```
server {
    listen 8080;
    server_name localhost;

    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

### Custom HTML File:

Create a folder called `html` in the same directory as the `Dockerfile` and place your HTML content inside this folder. For example, create a basic `index.html` file:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Custom Nginx Page</title>
</head>
<body>
    <h1>Hello, this is a custom Nginx page!</h1>
</body>
</html>
```

### Dockerfile:

```docker
# Use the official Nginx base image
FROM nginx:latest

# Remove the default Nginx configuration
RUN rm /etc/nginx/conf.d/default.conf

# Copy custom Nginx configuration
COPY ./nginx.conf /etc/nginx/conf.d/

# Copy custom HTML content
COPY ./html /usr/share/nginx/html

# Expose port 8080
EXPOSE 8080

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
```

- The **`-g`** flag in Nginx allows you to pass configuration commands directly to Nginx.
- **Foreground mode** (`daemon off`) is crucial for keeping the Docker container running, as Docker manages containers based on the state of the primary process.
- Running Nginx in the background (without `daemon off`) would cause the container to stop immediately, because Docker wouldn’t detect any active process.
- This command ensures that Nginx runs as the primary, foreground process inside the container, keeping it alive and making log management easier.

### Steps to Build and Run the Image to create the container from the image:

1. **Build the Docker image**:
    - Run the following command to build the Docker image:
    
    ```bash
    docker build -t custom-nginx .
    ```
    
2. **Run the container**:
    - To run the container and map the container's port 8080 to the host's port 8080, use the following command:
    
    ```bash
    docker run -d -p 8080:8080 custom-nginx
    ```
    

### Access the HTML File:

**Open your web browser** and go to `http://localhost:8080`.