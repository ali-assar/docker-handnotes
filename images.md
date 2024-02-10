## Images

### What is an Image?

An image in Docker is a lightweight, standalone, executable package that includes everything needed to run a piece of software, including the code, runtime, libraries, environment variables, and configuration files. It consists of both binary dependencies and metadata, encapsulated in a single unit.

### How to Create an Image via Dockerfile

You can create a custom Docker image using a Dockerfile, which is a text file that contains instructions for building the image. Here's a basic example of creating a custom image using a Dockerfile:

#### Step 1: Create a Dockerfile

Create a file named `Dockerfile` in your project directory. This file will contain instructions for building your custom image.

```Dockerfile
# Use an existing base image
FROM ubuntu:latest

# Set environment variables
ENV APP_HOME /myapp

# Set the working directory inside the container
WORKDIR $APP_HOME

# Copy application files into the container
COPY . $APP_HOME

# Install dependencies and configure the environment
RUN apt-get update && \
    apt-get install -y <package1> <package2> && \
    <any other necessary setup commands>

# Expose any necessary ports
EXPOSE 80

# Define the command to run the application
CMD ["<command to start the application>"]
```

Replace `<package1>`, `<package2>`, `<any other necessary setup commands>`, and `<command to start the application>` with your actual dependencies and startup commands.

#### Step 2: Build the Image

Navigate to the directory containing your Dockerfile and execute the following command to build the Docker image:

```bash
docker build -t my_custom_image .
```

This command builds a Docker image based on the instructions in your Dockerfile and tags it with the name `my_custom_image`.

#### Step 3: Run a Container from the Custom Image

Once the image is built, you can run a container from it using the following command:

```bash
docker run -d -p 8080:80 my_custom_image
```

This command starts a container based on the `my_custom_image` image, exposes port `80` from the container to port `8080` on the host, and runs the container in detached mode (`-d`).
