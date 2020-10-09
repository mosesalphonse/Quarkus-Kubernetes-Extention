# Quarkus - Kubernetes extention - Sample project

This project uses Quarkus with Kubernetes extentin.

#  Prerequisites

```
* Apache Maven 3.6.3 or above
* Java version: 11 or above
* Docker Version: 19.03.13 or above
```

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```
./mvnw quarkus:dev
```

## Packaging and running the application in Local

The application can be packaged using `./mvnw package`.

It produces the `kubernetes-quickstart-1.0-SNAPSHOT-runner.jar` file in the `/target` directory.


The application is now runnable using `java -jar target/kubernetes-quickstart-1.0-SNAPSHOT-runner.jar`.


## Creating a native executable

You can create a native executable using: `./mvnw package -Pnative`.

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: `./mvnw package -Pnative -Dquarkus.native.container-build=true`.

You can then execute your native executable with: `./target/kubernetes-quickstart-1.0-SNAPSHOT-runner`

## Note: 
This code(both JVM and native) are tested on Google Cloud Platform
