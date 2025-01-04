# To run the whole app
## A pom file should be created at the root project, with the jib plugin and specifying the modules (microservices)
1. All modules in the project are compiled and placed in the target/ dir of each module
2. Docker images are created for each module that has the jib plugin, the default name of the generated image is moduleName:moduleVersion, but it could be specified in the pom file
3. The docker-Compose up is then called to created the containers from the generated images
>mvn compile jib:dockerBuild && docker-compose up

## To run one micro-service
>mvn spring-boot:run

## To build, test and package a micro-service
>mvn clean install


# To build a docker image of a micro-service locally
## the image is built and installed locally
1. Builds the application.
2. Constructs a Docker container image.
3. Loads the image into the local Docker daemon
>mvn compile jib:DockerBuild

# To build a docker image of a micro-service remotely 
## the image is built and directly pushed to a remote container registry
1. Builds the application.
2. Constructs a Docker container image.
3. Pushes the image directly to a configured remote container registry (e.g., Docker Hub, AWS ECR, GCP Container Registry).
>mvn compile jib:build