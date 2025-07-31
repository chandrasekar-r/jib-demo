# Sample Java Jib Project

This is a sample Java Spring Boot project that demonstrates how to use Google's Jib tool for containerizing Java applications without writing Dockerfiles.

## What is Jib?

Jib is a Maven and Gradle plugin that builds optimized Docker and OCI images for Java applications without requiring a Dockerfile. It's developed by Google and offers several advantages over traditional Docker builds.

## Project Structure

```
sample-java-jib-project/
├── pom.xml                          # Maven configuration with Jib plugin
├── src/
│   └── main/
│       └── java/
│           └── com/
│               └── example/
│                   └── demo/
│                       └── DemoApplication.java  # Simple Spring Boot app
└── README.md
```

## Building and Running

### Build the Docker Image with Jib

```bash
# Build to local Docker daemon
mvn compile jib:dockerBuild

# Build and push to a registry (requires registry configuration)
mvn compile jib:build

# Build to a tar file
mvn compile jib:buildTar
```

### Run the Container

```bash
# Run the containerized application
docker run -p 8080:8080 sample-java-app:latest

# Test the application
curl http://localhost:8080
```

## Jib Configuration Explained

The Jib plugin is configured in the `pom.xml` file with the following key sections:

- **Base Image (`from`)**: The base image to use (eclipse-temurin:17-jre-alpine)
- **Target Image (`to`)**: The name and tags for the output image
- **Container Config**: JVM flags, exposed ports, and other runtime settings

## Benefits of Using Jib

1. **No Dockerfile needed**: Jib handles the containerization automatically
2. **Fast builds**: Only changed layers are rebuilt and pushed
3. **Reproducible builds**: Same inputs always produce the same image
4. **Security**: Uses distroless base images by default
5. **Integration**: Works seamlessly with Maven/Gradle build process
