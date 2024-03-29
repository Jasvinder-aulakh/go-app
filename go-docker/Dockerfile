# Dockerfile References: https://docs.docker.com/engine/reference/builder/

# Start from golang v1.11 base image
FROM golang:1.12.6-alpine3.10

# Add Maintainer Info
LABEL maintainer="Jasvinder Singh 'jass_rhce@live.hk'"

# Build Args
ARG APP_NAME=go-docker
ARG LOG_DIR=/${APP_NAME}/logs

# Create Log Directory
RUN mkdir -p ${LOG_DIR}

# Environment Variables
ENV LOG_FILE_LOCATION=${LOG_DIR}/app.log 

# Set the Current Working Directory inside the container
WORKDIR $GOPATH/src/github.com/go-app/go-docker

# Copy everything from the current directory to the PWD(Present Working Directory) inside the container
COPY ./ ./

# Download all the dependencies

RUN go get -d -v ./...

# Install the package
RUN go install -v ./...

# This container exposes port 8080 to the outside world
EXPOSE 8080

# Run the executable
CMD [ "go-docker" ]