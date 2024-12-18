# config-server

## Description

This is a simple server that uses Spring Cloud Config and reads the configs from [config-repo](https://github.com/octavian-h/config-repo)

## Requirements

To build and run this application you need to install the followings:

- JDK 21 or later
- Maven

On MacOS you can use these commands (assuming that [Homebrew](https://brew.sh/) is already installed:

```bash
brew install openjdk@21
brew install --ignore-dependencies maven
```

## Usage

Run the following commands:

```bash
mvn clean package
cd target/
java -jar server.jar
```
