# Java Openjdk Quarkus - Wildfly Microservices S2i Images


## CentOS - Alpine - Fedora - Debian
## Openjdk 11,8

![Docker Stars](https://img.shields.io/docker/stars/mvilche/java-microservices-s2i.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/mvilche/java-microservices-s2i.svg)
![Docker Automated](https://img.shields.io/docker/cloud/automated/mvilche/java-microservices-s2i)
![Docker Build](https://img.shields.io/docker/cloud/build/mvilche/java-microservices-s2i)


# Features

- Non-root
- Openshift Ready!
- S2i build images
- Maven
- Jolokia java monitoring
- Support Wildfly Throntail, Wildfly Bootable, Quarkus

### Deploy Environments 


| Environment | Details |
| ------ | ------ |
| TIMEZONE | Set Timezone (America/Montevideo, America/El_salvador) |
| JAVA_OPTS | set JAVA_OPTS options|
| APP_OPTIONS | set extra arguments when application start |
| WAITFOR_HOST | set name host |
| WAITFOR_PORT | set port for WAITFOR_HOST |



### Build Environments 


| Environment | Details |
| ------ | ------ |
| MVN_OPTS | Maven options  |
| NEXUS_MIRROR_URL | Nexus repository override repository in pom.xml |
| QUARKUS_PACKAGE_TYPE | Quarkus package type values: fast-jar, uber-Jar |


### How use in Openshift

```console

oc process -f https://raw.githubusercontent.com/mvilche/java-microservices-s2i/master/java-openjdk-microservices-s2i-template-dev.yaml \ 
-p APP_NAME=myapp \
-p VERSION_JDK=11 \ 
-p REPO_GIT=https://github.com/myuser/java-sample-app.git
-p SOURCE_SECRET=github | oc create -f -

```


### Generate builder image

```console

 docker build -t java-openjdk-microservices-s2i:openjdk11-jdk -f openjdk11/Dockerfile.jdk myapp

```

### Java application image use s2i

```console

s2i build https://github.com/myuser/java-sample-app.git java-openjdk-microservices-s2i:openjdk11-jdk myapp:latest --incremental

```


### Run application

```console

docker run -p 8080:8080 myapp:latest

```

### How use s2i

```console

https://github.com/openshift/source-to-image

```

License
----

Martin vilche
