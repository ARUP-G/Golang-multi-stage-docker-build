# Multi Stage Docker Build
## Multistaged Docker Build
This repository demonstrates the use of multistage Docker builds to create efficient and lightweight Docker images for your applications. Multistage builds allow you to use multiple FROM statements in your Dockerfile, creating multiple image layers, each with its own set of dependencies and tools.

## Overview
In traditional Docker builds, each instruction in the Dockerfile creates a new layer in the image. As the number of layers increases, so does the size of the final image. Multistage builds address this issue by allowing you to use multiple base images and copy only the necessary artifacts from one stage to another. The final image only contains the files and dependencies needed to run the application.

## Dockerfile Explanation
The Dockerfile in this repository demonstrates a basic multistage build for a Golang application. Here's a breakdown of the stages:

### Build Stage:

Uses a Ububtu base image to build the application.
Installs dependencies and builds the application.
Outputs the compiled application in the directory.

## Getting Started
To use multistage builds for this projects, follow these steps:

### Step 1: Clone the Repository

Clone this repository to your local machine:

```bash
    git clone https://github.com/ARUP-G/Golang-multi-stage-docker-build.git
    
    # To build without multistage dockerfile
    cd Golang-multi-stage-docker-build/dockerfile-without-multistage
    
    # To build multistage dockerfile
    cd Golang-multi-stage-docker-build/Multistaged-docker-file
```

### Step 2A: Build the Docker Image without multistage

Build the Docker image using the provided *Dockerfile*:
```bash
    docker build -t without-multistage-app .
```
<p align="center">
 <img src="without-multistage-build.png?raw=true" alt="without-multistage-build" width="100%" height="50%" />
</p>

### Step 3A: Run Docker Container

Run a Docker container from the image you just built:
```bash
    docker run -p 8080:8081 -it without-multistage-app
```
'*-p*' maps port 8081 from the container to port 9000 on your host machine.

### Step 4A: Check image size
```bash
    docker images
```
Find '*without-multistage-app*' named image and note the image **size**.

<p align="center">
 <img src="image-size-1.png?raw=true" alt="image size 1" width="80%" height="50%" />
</p>

### Step 2B: Build the Docker Image with multistage

Build the Docker image using the provided *Dockerfile*:
```bash
    docker build -t multistage-app .
```
<p align="center">
 <img src="multistage-app-build.png?raw=true" alt="multistage-app-build" width="100%" height="50%" />
</p>

### Step 3B: Run Docker Container

Run a Docker container from the image you just built:
```bash
    docker run -p 8080:8090 -it without-multistage-app
```
'*-p*' maps port 8081 from the container to port 9000 on your host machine.

### Step 4B: Check image size
```bash
    docker images
```
Find '*multistage-app*' named image and note the image **size**.

<p align="center">
 <img src="image-size-2.png?raw=true" alt="image size 2" width="80%" height="50%" />
</p>

## Observation
### Non-Multistage Docker Image:

**Image Size**: Larger due to including build tools and unnecessary dependencies.
### Multistage Docker Image:

**Image Size** : Smaller, as only essential artifacts are included in the final stage.

## Conclusion

The multistage Docker build resulted in a significantly smaller image size compared to the non-multistage build. This reduction in size is attributed to the elimination of unnecessary files and dependencies in the final image. Multistage builds prove to be an effective strategy for optimizing Docker images, especially when striving for minimal container size and improved resource efficiency.

Consider using multistage builds in your projects to benefit from smaller image sizes, faster deployments, and reduced resource consumption.

## Customization
Feel free to modify the Dockerfile and the application code to suit your specific project requirements. Adjust the base images, dependencies, and build steps according to the needs of your application.

## Contributing
If you have any suggestions, improvements, or bug fixes, feel free to open an issue or create a pull request. Your contributions are highly appreciated!