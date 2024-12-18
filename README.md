# config-server

## Description

This is a simple server that uses Spring Cloud Config and reads the configs from [config-repo](https://github.com/octavian-h/config-repo).

## Requirements

To build and run this application you need to install the followings:

- JDK 21 or later
- Maven
- Podman Compose (a tool that knows how to run docker-compose.yml)

On MacOS you can use these commands (assuming that [Homebrew](https://brew.sh/) is already installed:

```bash
brew install openjdk@21
brew install --ignore-dependencies maven
brew install podman-compose
```

## Usage

Firstly you need to start the container engine with:

```bash
podman machine start
```

If docker-compose.yml was changed, or it is the first time then (re)create the services with

```bash
podman-compose up -d
```

Otherwise, just start the pod with the existing containers with:

```bash
podman pod start "pod_config-server"
```

After the pod is started you can build and run the app with:

```bash
mvn clean package
java -jar ./target/server.jar
```

When a change is done on [config-repo](https://github.com/octavian-h/config-repo) you need to call /monitor to announce the change to all consumers.
Example:

```http request
POST http://127.0.0.1:8888/monitor
Content-Type: application/x-www-form-urlencoded

path = second-service
```