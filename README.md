# Quarkus - Kubernetes extention - Sample project

This project uses Quarkus with Kubernetes extentin.

#  Prerequisites

```
* Apache Maven 3.6.3 or above
* Java version: 11 or above
* Docker Version: 19.03.13 or above
* Kubernetes Cluster version v1.17.9 or more
```

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```
./mvnw quarkus:dev
```

## Packaging and running the application in Local using JVM

The application can be packaged using `./mvnw package`.

It produces the `kubernetes-quickstart-1.0-SNAPSHOT-runner.jar` file in the `/target` directory.


The application is now runnable using `java -jar target/kubernetes-quickstart-1.0-SNAPSHOT-runner.jar`.


## Packaging and running the application in Local using Native Image

You can create a native executable using: `./mvnw package -Pnative`.

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: `./mvnw package -Pnative -Dquarkus.native.container-build=true`.

You can then execute your native executable with: `./target/kubernetes-quickstart-1.0-SNAPSHOT-runner`


## Create Kubernates resources, push the Docker image into GCR/Docker Hub and deploy it into Kubernetes Cluster

Make Sure the below properties(in application.properties)

```
quarkus.container-image.registry=gcr.io	//gcr, by default its docker hub
quarkus.container-image.group=google-projectname // google account name
#quarkus.container-image.registry=gcr.io	//in case of Docker Hub, remove this key, default registry is Docker Hub
#quarkus.container-image.group=dockerhub-username // Docker Hub account username
quarkus.container-image.name=kubernetes-quarkus // image name
quarkus.container-image.tag=1 //image tag
quarkus.kubernetes.service-type=load-balancer
```

#Before build, login into docker registry

docker login gcr.io // if you are running within google cloud, it is not required

docker login // by default, it will ask docker hub credentials

## JVM Mode:

```
mvn clean package -Dquarkus.container-image.push=true // verify the image in GCR

kubectl apply -f target/kubernetes/kubernetes.yml
```

## Native Image

```
mvn package -Pnative -Dquarkus.native.container-build=true -Dquarkus.container-image.push=true

kubectl apply -f target/kubernetes/kubernetes.yml
```

Now you can see the above Kubernetes resources, should be running in your cluster.


## Note: 
This code(both JVM and native) are tested on Google Cloud Platform
